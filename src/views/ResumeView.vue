<template>
  <div class="container">
    {{ experiences }}
    <hr>
    {{ educations }}
    <hr>
    {{ skills }}
  </div>
</template>

<script>
import axios from "axios"

  export default {
    data() {
      return {
        experiences: [],
        educations: [],
        skills: [],
        errors: [],
      }
    },
    created() {
      this.indexExperiences();
      this.indexEducations();
      this.indexSkills();
    },
    methods: {
      showStudent() {
        axios.get(`/students/${id}.json`)
        .then((res)=> {
          this.students.push(res.data)
        })
        .catch((error)=> {
          this.errors.push(error.response)
        })
      },
      indexExperiences() {
        axios.get('/experiences.json')
        .then((res)=> {
          this.experiences.push(res.data)
        })
        .catch((error)=> {
          this.errors.push(error.response)
        })
      },
      indexEducations() {
        axios.get('/educations.json')
        .then((res)=> {
          this.educations.push(res.data)
        })
        .catch((error)=> {
          this.errors.push(error.response)
        })
      },
      indexSkills() {
        axios.get('/skills.json')
        .then((res)=> {
          this.skills.push(res.data)
        })
        .catch((error)=> {
          this.errors.push(error.response)
        })
      },
    },
  }
</script>

<style>
  
</style>