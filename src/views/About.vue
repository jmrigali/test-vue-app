<template>
  <div class="about">
    <h1>This is Server Information</h1>
    <!-- <h2>{{ info.data }}</h2> -->
    <p>{{ url }}</p>
    <p>{{ body }}</p>
    <p>{{ success }}</p>

    <br />

    <div>
      <CreateWorkout></CreateWorkout>
    </div>
  </div>
</template>
<script>
  import axios from 'axios'
  import CreateWorkout from '../components/CreateWorkout.vue'

  export default {
    name: 'createWorkout',
    components: {
      CreateWorkout
    },
    data() {
      return {
        info: '',
        url: '',
        body: '',
        success: ''
      }
    },
    mounted() {
      if (this.$store.state.user) {
        const jwt = this.$store.state.user
          .getSignInUserSession()
          .getIdToken()
          .getJwtToken()

        const config = {
          headers: {
            authorization: jwt
          }
        }
        axios
          .get('https://f4hn4p46j4.execute-api.us-west-2.amazonaws.com/v1/workouts', config)
          .then((val) => {
            console.log('Value', val)
            this.info = val
            this.success = val.data.success
            this.url = val.data.url
            this.body = val.data.body
          })
          .catch((err) => console.log(err))
      }
    }
  }
</script>
