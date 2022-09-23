<template>
  <div class="container mt-5 text-center">
    <h3>{{ message }}</h3>
  </div>

</template>

<script>
import {onMounted, ref} from "vue";
import axios from "axios";

export default {
  name: "Home",
  setup(){
    const message = ref('You are not logged in');

    onMounted(async () => {
      const {data} = await axios.get('http://localhost:8000/api/user');
      message.value = `Hi ${data.first_name} ${data.last_name}`
    })
    return{
      message
    }
  }
}
</script>