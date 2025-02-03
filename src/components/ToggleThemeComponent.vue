<template>
    <div class="switch-div">
        <label class="switch">
        	<!-- bind the checked attribute to the isDark property -->
            <input type="checkbox" :checked="isDark" @click="toggleTheme()">
            <span class="slider round"></span>
        </label>
    </div>
</template>
<script setup>
import { useDark, useToggle } from '@vueuse/core';

// checks localstorage to see if user has a selected preference
// toggle class=dark on the element with id=app
const isDark = useDark({
    selector: ".main-div",
    attribute: "class",
    valueDark: "dark",
    valueLight: "light"
})
const toggleTheme = useToggle(isDark)
</script>
<style lang="css" scoped>
.switch-div {
    position: absolute;
    right: 18px;
    top: 10px;
    padding: 8px;
}

/* switch styles */
/* The switch - the box around the slider */
.switch {
    position: relative;
    display: inline-block;
    width: 60px;
    height: 25px;
}

/* Hide default HTML checkbox */
.switch input {
    opacity: 0;
    width: 0;
    height: 0;
}

/* The slider */
.slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #ccc;
    -webkit-transition: .4s;
    transition: .4s;
}

.slider:before {
    position: absolute;
    content: "";
    height: 20px;
    width: 20px;
    left: 4px;
    bottom: 2.5px;
    background-color: white;
    -webkit-transition: .4s;
    transition: .4s;
}

input:checked+.slider {
    background-color: #00B612;
}

input:focus+.slider {
    box-shadow: 0 0 1px #00B612;
}

/* how the switch slider moves when turned on */
input:checked+.slider:before {
    -webkit-transform: translateX(32px);
    -ms-transform: translateX(32px);
    transform: translateX(32px);
}

/* Rounded sliders */
.slider.round {
    border-radius: 34px;
}

.slider.round:before {
    border-radius: 50%;
}
</style>