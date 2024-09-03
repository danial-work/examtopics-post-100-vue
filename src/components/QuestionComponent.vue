<template>
  <div>
    <h2 class="text_left">
      <a v-if="q_l[Object.keys(q_l)[0]]" :href="q_l[Object.keys(q_l)[0]]" target="_blank">Question {{ Object.keys(q_l)[0] }}</a>
      <p v-else>Question {{ Object.keys(q_l)[0] }}</p>
    </h2>
    <iframe v-if="q_l[Object.keys(q_l)[0]]" :src="q_l[Object.keys(q_l)[0]]"></iframe>
    <p v-else>No question available</p>
    
  </div>
</template>

<script>
export default {
  name: 'QuestionComponent',
  props: {
    q_l: Object
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

div {
  width: 90%;
  margin: 0 auto;
}

.text_left {
  text-align: left;
}

iframe{
  width: 100%;
  height: 98vh;
}
</style>
