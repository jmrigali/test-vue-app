<template>
  <div>
    <!-- <h2>Random Workout</h2> -->
    <button @click="makeRoutine">Random Workout</button>

    <div v-for="exercise in workouts" :key="exercise.name">3 x {{ exercise.name }}</div>
  </div>
</template>
<script>
  export default {
    data() {
      return {
        workouts: [],
        legs: [
          { name: 'Overhead Squats' },
          { name: 'Forward Lunges' },
          { name: 'Reverse Lunges' },
          { name: 'Lateral Lunges' },
          { name: 'Curtsy Lunge' },
          { name: 'Back Squats' },
          { name: 'Sumo Squats' },
          { name: 'Bulgarian Split Squat' },
          { name: 'Glute Bridge' },
          { name: 'Glute Bridge March' },
          { name: 'Quadraped Hip Extension' },
          { name: 'Single Leg Deadlift' },
          { name: 'Single Leg Glute Bridge' },
          { name: 'Calf Raise' }
        ],
        core: [
          { name: 'Plank' },
          { name: 'Crunches' },
          { name: 'Plank Up-Downs' },
          { name: 'Bird-Dogs' },
          { name: 'Bicycle Crunches' },
          { name: 'V-Ups' },
          { name: 'Hollowman' },
          { name: 'V-Sit' },
          { name: 'Superman Pull' },
          { name: 'Leg Raises' },
          { name: 'Plank Knee Crosses' },
          { name: 'Elbow Plank Twists' },
          { name: 'Plank Shoulder Taps' },
          { name: 'Side Plank' }
        ],
        upperBody: [
          { name: 'Pushups' },
          { name: 'Tricep Pushups' },
          { name: 'Tricep Dips' },
          { name: 'I-Y-T Raises' },
          { name: 'Lateral Plank Walk' },
          { name: 'Decline Pushups' },
          { name: 'Arm Circles' }
        ],
        stretches: [
          { name: 'Head Roll' },
          { name: 'Shoulder Shrugs' },
          { name: 'Pectoral Wall Stretch' },
          { name: 'Side Stretch' },
          { name: 'Arm Stretch' },
          { name: 'Quad Stretch' },
          { name: 'Hamstring Stretch' },
          { name: 'Downward Dog' },
          { name: 'Cobra' },
          { name: 'Hip Flexor Lunge Stretch' },
          { name: 'Butterfly Adducter Stretch' },
          { name: 'Pidgeon Stretch' },
          { name: 'Calf Stretch' }
        ],
        plyos: [
          { name: 'Jump Squat' },
          { name: 'Skater Jump' },
          { name: 'Jump Lunge' },
          { name: 'Frog Jump' },
          { name: 'Burpees' },
          { name: 'Mountain Climbers' },
          { name: 'Bear Crawl' }
        ]
      }
    },
    mounted() {
      this.workouts = this.makeRoutine()
    },
    methods: {
      makeRoutine() {
        console.log('in workout routine')
        const workoutArray = []
        workoutArray.push(this.findRandomValue(this.legs))
        workoutArray.push(this.findRandomValue(this.core))
        workoutArray.push(this.findRandomValue(this.upperBody))
        workoutArray.push(this.findRandomValue(this.plyos))
        this.workouts = workoutArray
      },
      findRandomValue(workoutArray) {
        return workoutArray[Math.floor(Math.random() * workoutArray.length)]
      }
    }
  }
</script>
<style>
  p {
    color: green;
  }
</style>
