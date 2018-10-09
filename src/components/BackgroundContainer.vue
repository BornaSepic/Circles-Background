<template>
  <div
    class="wrapper"
    @click="userAddNewCircle()"
    @mousemove="hightlightCircles()">
    <BackgroundCircle 
      v-for="(circle, index) in circles"
      :key="index"
      :render-info="circle"
    />
  </div>
</template>

<script>
import BackgroundCircle from './BackgroundCircle.vue'
const startingCircles = 5;




export default {
    name: 'BackgroundContainer',
    components: {
        BackgroundCircle
    },
    data: function() {
        return {
            circles: [],
            screenHeight: window.innerHeight,
            screenWidth: window.innerWidth
        }
    },
    mounted(){
        for (let i = 0; i < startingCircles; i++) {
            const element = this.renderCircle();
            this.circles.push(element);
        }
        setInterval(function(){ this.addNewCircle() }.bind(this), 1000);
        this.$nextTick(() => {
            window.addEventListener('resize', () => {
                this.screenHeight = window.innerHeight
                this.screenWidth = window.innerWidth
            });
        });
    },
    methods:{
        renderCircle: function() {
            const circleDimensions = Math.floor(Math.random() * 35) + 15;
            const circleXcoordinate = Math.floor(Math.random() * ((this.screenWidth - circleDimensions * 1.1)));
            const circleYcoordinate = Math.floor(Math.random() * ((this.screenHeight - circleDimensions * 1.1)));
            return {
                circleDimensions: circleDimensions,
                X: circleXcoordinate,
                Y: circleYcoordinate,
                hoverEffect: false
            }
        },
        addNewCircle: function() {
            if (this.circles.length <= 120) {
                const newCircle = this.renderCircle();
                this.circles.push(newCircle);
            }
            return true
        },
        userAddNewCircle: function() {
            const circleDimensions = Math.floor(Math.random() * 35) + 15;
            const xCoordinate = event.clientX;
            const yCoordinate = event.clientY;
            const newCircle = {
                circleDimensions: circleDimensions,
                X: xCoordinate,
                Y: yCoordinate,
                hoverEffect: false
            }
            this.circles.push(newCircle);
        },
        hightlightCircles: function() {
            const mouseXcoordinate = event.clientX;
            const mouseYcoordinate = event.clientY;

            this.circles.forEach(circle => {
                if (Math.abs(mouseXcoordinate - circle.X) < 100 && Math.abs(mouseYcoordinate - circle.Y) < 100) {
                    circle.hoverEffect = true;
                } else {
                    circle.hoverEffect = false;
                }
            });
        }
    }
}
</script>

<style>
    body{
        overflow: hidden;
    }
    .wrapper{
        background: rgb(255, 255, 255);
        width: 100%;
        max-height: 90vh;
        height: 100%;
    }
</style>
