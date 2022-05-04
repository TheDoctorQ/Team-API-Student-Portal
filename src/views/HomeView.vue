<script>
export default {
  data: function () {
    return {
      message: "Welcome to the Student Portal!",
    };
  },
  created: function () { },
  methods: {},
};
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <img id="gateroom"
      src="https://steamuserimages-a.akamaihd.net/ugc/919178208542519125/A77AA08939CF00B5F1B81BA1198992332DB77096/?imw=637&imh=358&ima=fit&impolicy=Letterbox&imcolor=%23000000&letterbox=true" />
    <h3>Please <a href="/login">login</a> to view your resume or capstone project.</h3>

  </div>
</template>

<style>
body {
  background-color: #DBF9FC;
}
</style>