<template>
  <div class="hello">
 <h1>cdsmk</h1>
<p>moin</p>
<div class="flex justify-evenly">
  <div>1</div>
  <div>2</div>
  <div>3</div>
</div>
<p class="text-9xl">The quick brown fox ...</p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
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
</style>
