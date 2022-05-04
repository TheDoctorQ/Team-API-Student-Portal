<script>
import axios from 'axios'
export default {
  data: function () {
    return {
      message: "Capstone",
      capstones: [],
      capstoneId: null,
      errors: [],
    };
  },
  created: function () {
    this.indexCapstone();
  },
  methods: {
    indexCapstone() {
      axios.get('/capstones.json')
      .then((res)=> {
        this.capstones.push(...res.data);
        this.capstoneId = res.data[0].id
      })
      .catch((error)=> {
        this.errors.push(error.response);
      })
    },
    updateCapstone() {
      let id = this.capstoneId
      console.log(id)
      axios.patch(`/capstones/${id}.json`, ...this.capstones)
      .then((res)=> {
        this.capstones.push(...res.data);
      })
      .catch((error)=> {
        this.errors.push(error.response);
      })
    },
    rerouteHome() {
      this.$router.push('/home');
    },
  },
};
</script>

<template>
  <div class="home">
    <form action="">
      <div v-for="capstone in capstones" :key="capstone.id">
        <p>id: <input type="text" v-model="capstone.id"></p>
        <p>student_id: <input type="text" v-model="capstone.student_id"></p>
        <p>name: <input type="text" v-model="capstone.name"></p>
        <p>description: <input type="text" v-model="capstone.description"></p>
        <p>url: <input type="text" v-model="capstone.url"></p>
        <p>screenshot: <input type="text" v-model="capstone.screenshot"></p>
      </div>
      <button @click="rerouteHome()">go back</button>
      <button @click="updateCapstone()">update</button>
    </form>
  </div>
</template>

<style>

</style>