<template>
  <div>
    <h2>Create Workout</h2>
    <input v-model="workout" type="text" placeholder="Workout Name" /><br />
    <button @click="submit">Submit</button>
  </div>
</template>
<script>
  import axios from 'axios'

  export default {
    data() {
      return {
        workout: ''
      }
    },
    methods: {
      submit() {
        if (this.$store.state.user) {
          const jwt = this.$store.state.user
            .getSignInUserSession()
            .getIdToken()
            .getJwtToken()

          const config = {
            headers: {
              authorization: jwt
            },
            body: { workout: this.workout }
          }

          axios
            .post('https://f4hn4p46j4.execute-api.us-west-2.amazonaws.com/v1/workouts', config)
            .then((val) => {
              console.log('Value', val)
            })
            .catch((err) => console.log(err))
        }
      }
    }
  }
</script>
<style>
  input {
    margin: 10px;
    padding: 16px;
  }
</style>
