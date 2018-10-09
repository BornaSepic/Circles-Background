<template>
  <div
    :style = "{ height: renderInfo.circleDimensions + 'px', width: renderInfo.circleDimensions + 'px', left: renderInfo.X + 'px', top: renderInfo.Y + 'px'}"
    :class="{hovered: renderInfo.hoverEffect}"
    class="circle circle-created" /> 
</template>

<script>
    export default {
        name: 'BackgroundCircle',
        props: {
            renderInfo: {
                type: Object,
                default: () => ({})
            }
        }
    }
</script>

<style>
    .circle{
        border: 0px solid;
        border-radius: 50%;
        position: absolute;
        background: cyan;
        animation: created 2s, moving 7s infinite;
    }
    .circle.hovered{
        animation: created 2s, moving 7s infinite, fade 1s ;
    }
   

    @keyframes moving {
        0%  { transform: translate(0px, 0px); background: none;}
        20%  {  background: cyan}
        50% {  background: purple} 
        95% { background: #ffe6ea } 
        100% { transform: translate(55%, 100%); background: none }
    }
    @keyframes created {
        0%  { height: 0px; width: 0px;}
    }
    @keyframes fade {
        0% {opacity: 1}
        100% {opacity: 0.5}        
    }
</style>
