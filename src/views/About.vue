<template>
  <div class="about">
    <h1>This is Server Information</h1>
    <h2>{{ info.data }}</h2>
  </div>
</template>
<script>
  import axios from 'axios'
  export default {
    data() {
      return {
        info: ''
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
          .then((val) => (this.info = val))
          .catch((err) => console.log(err))
      }
    }
  }
</script>
