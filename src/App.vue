<template>
    <div class="main-div">
        <ToggleComponent />
      <transition name="time" appear>
        <TimeDisplay />
      </transition>
      <DevComponent />
    </div>
</template>
<script>
import TimeDisplay from './components/TimeDisplay.vue'
import DevComponent from './components/DevComponent.vue'
import ToggleComponent from './components/ToggleThemeComponent.vue'

export default {
    name: 'App',
    components: {
        TimeDisplay, DevComponent, ToggleComponent
    }

}
</script>
<style>
@font-face {
    font-family: "tragic";
    src: url('~@/assets/fonts/custom-font.ttf');
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

#app {
    font-family: "tragic", Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    width: 100vw;
    height: 100vh;
}
.main-div {
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

}

/* toggle styles for the background color */
.light {
    background: #FFFFFF;
    color: red;
}
.dark {
    background: #000000;
}

/* enter styles for the time display box */
.time-enter-from {
    opacity: 0;
    transform: scale(0);
}

.time-enter-to {
    opacity: 1;
    transform: scale(1);
}

/* leave styles for the time display box */
.time-leave-from {
    opacity: 1;
    transform: scale(1);
}

.time-leave-to {
    opacity: 0;
    transform: scale(0);
}

.time-enter-active,
.time-leave-active {
    transition: all 1s ease;
}
</style>