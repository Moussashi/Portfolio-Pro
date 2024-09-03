<template>
<!-- Page Transition -->
  <div class="content">
      <router-view v-slot="{ Component, route }">
          <transition name="fade" mode="out-in">
            <div :key="route.fullPath">
              <component :is="Component" />
            </div>
          </transition>
      </router-view>
  </div>

</template>

<style scoped>
html, body {
  padding: 0;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  font-family: 'Courier New', Courier, monospace;
}  
  .fade-enter-from {
    opacity: 0;
    transform: translateX(100px);
  }
  .fade-enter-active {
    transition: all 0.3s ease-out;
  }

  .fade-leave-to {
    opacity: 0;
    transform: translateX(-100px);
  }

  .fade-leave-active {
    transition: all 0.3s ease-in;
  }
</style>

/* On click add a class to the buttons to recreate the hover final state*/

/* same as above for the work component, to know wich one is active */