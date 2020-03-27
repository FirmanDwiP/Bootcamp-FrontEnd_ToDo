<template>
  <div class="home">

    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import List from '@/components/List.vue'

export default {
  name: "List",
  components: {
    List
  }
};
</script>
