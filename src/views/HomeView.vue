<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <chat />
    
  </div>
</template>

<script>
// @ is an alias to /src
import chat from "../components/chat"

export default {
  name: 'HomeView',
  components: {
    chat
  }
}
</script>
