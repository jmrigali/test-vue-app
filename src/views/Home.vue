<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <br />
    <div>
      <Workout></Workout>
    </div>
  </div>
</template>

<script>
  // @ is an alias to /src
  import HelloWorld from '@/components/HelloWorld.vue'
  import Workout from '@/components/Workout.vue'
  export default {
    name: 'home',
    components: {
      HelloWorld,
      Workout
    }
  }
</script>
