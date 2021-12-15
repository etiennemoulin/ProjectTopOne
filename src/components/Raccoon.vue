<template>
  <div class="Raccoon">
      <img alt="Raccoon cute" src="../../img/raccoon.png">
  </div>
</template>
<script>
export default {
  name: 'Raccoon',
  props: {
    msg: String
  }
}
</script>

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
</style>
