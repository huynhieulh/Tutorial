<!-- <script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from '@/components/HelloWorld.vue'
</script> -->
<template>
    <header>
        <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

        <div class="wrapper">
        <HelloWorld msg="You did it!" />

        <nav>
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/about">About</RouterLink>
        </nav>
        <input type="checkbox" id="toggle" class="toggle--checkbox" v-model="toggle" true-value="dark" false-value="light" @change="changeMode">
        <label for="toggle" class="toggle--label">
        <span class="toggle--label-background"></span>
        </label>
        </div>
    </header>
</template>

<script>
import { RouterLink, RouterView } from 'vue-router';
import HelloWorld from '@/components/HelloWorld.vue';
export default{
    methods: {
        changeMode(e){
            // console.log("event: ", e);
            // console.log("this: ", this.toggle);
            // if(this.toggle == 'dark'){
                document.body.classList.toggle("dark__theme");
            // }
        }
    }
}
</script>

<style>
:root {
  /** sunny side **/
  --blue-background: #C2E9F6;
  --blue-border: #72cce3;
  --blue-color: #96dcee;
  --yellow-background: #fffaa8;
  --yellow-border: #f5eb71;
  /** dark side **/
  --indigo-background: #808fc7;
  --indigo-border: #5d6baa;
  --indigo-color: #6b7abb;
  --gray-border: #e8e8ea;
  --gray-dots: #e8e8ea;
  /** general **/
  --white: #fff;

  --animation-speed: 1s;
  --bg-color: #9ebbeb;
  --text-color: #111;
  --font: "Poppins", sans-serif;
}

.dark__theme {
  --bg-color: #808fc7;
  --text-color: #fff;
}

.background {
  position: absolute;
  left: 0;
  top: 0;
  background: var(--bg-color);
  z-index: -1;
  width: 100%;
  height: 100%;
  transition: all 250ms ease-in;
}
.toggle--checkbox {
  display: none;
}
.toggle--checkbox:checked {
  /** This will all flip from sun to moon **/
  /** Change the label color **/
}

.toggle--checkbox:checked + .toggle--label {
  background: var(--indigo-color);
  border-color: var(--indigo-border);
}
.toggle--checkbox:checked + .toggle--label .toggle--label-background {
  left: 60px;
  width: 5px;
}
.toggle--checkbox:checked + .toggle--label .toggle--label-background:before {
    width: 3px;
    height: 3px;
    top: -18px;
    left: -35px;
}
.toggle--checkbox:checked + .toggle--label .toggle--label-background:after {
    width: 3px;
    height: 3px;
    left: -45px;
    top: 0px;
}
.toggle--checkbox:checked + .toggle--label:before {
  background: var(--white);
  border-color: var(--gray-border);
  animation-name: switch;
  animation-duration: 350ms;
  animation-fill-mode: forwards;
    width: 40px !important;
    height: 40px;
    left: 50px !important;
}
.toggle--checkbox:checked + .toggle--label:after {
  transition-delay: 350ms;
  opacity: 1;
}
.toggle--label {
  /** Placeholder element, starting at blue **/
  width: 100px;
  height: 50px;
  background: var(--blue-color);
  border-radius: 100px;
  border: 5px solid var(--blue-border);
  display: flex;
  position: relative;
  transition: all 350ms ease-in;
  /** The sun cloud and moon stars **/
  /** Sun/Moon element **/
  /** Gray dots on the moon **/
}
.toggle--label-background {
  width: 8px;
  height: 5px;
  border-radius: 5px;
  position: relative;
  background: var(--white);
  left: 60px;
  top: 19px;
  transition: all 150ms ease-in;
}
.toggle--label-background:before {
  content: "";
  position: absolute;
  top: -5px;
  width: 25px;
  height: 5px;
  border-radius: 5px;
  background: var(--white);
  left: -12px;
  transition: all 150ms ease-in;
}
.toggle--label-background:after {
  content: "";
  position: absolute;
  top: 5px;
  width: 25px;
  height: 5px;
  border-radius: 5px;
  background: var(--white);
  left: -3px;
  transition: all 150ms ease-in;
}
.toggle--label:before {
  animation-name: reverse;
  animation-duration: 350ms;
  animation-fill-mode: forwards;
  transition: all 350ms ease-in;
  content: "";
  width: 41px;
  height: 41px;
  border: 5px solid var(--yellow-border);
  top: 0px;
  left: 0px;
  position: absolute;
  border-radius: 82px;
  background: var(--yellow-background);
}
.toggle--label:after {
  transition-delay: 0ms;
  transition: all 250ms ease-in;
  position: absolute;
  content: "";
  box-shadow: var(--gray-dots) -110px -12px 0 1px, var(--gray-dots) -114px 5px 0 -2px;
  left: 143px;
  top: 23px;
  width: 10px;
  height: 10px;
  background: transparent;
  border-radius: 50%;
  opacity: 0;
}

@keyframes switch {
  0% {
    left: 2px;
  }
  60% {
    left: 2px;
    width: 46px;
  }
  100% {
    left: 52px;
    width: 41px;
  }
}
@keyframes reverse {
  0% {
    left: 52px;
    width: 41px;
  }
  60% {
    left: 36px;
    width: 46px;
  }
  100% {
    left: 2px;
  }
}
</style>
