<template>
 <div>
  <div class="wrapper">
   <div v-for="(item, i) in forCount" v-bind:key="item">
    <span class="span">{{ i+1 }}</span> . {{ item.a }}
   </div>
  </div>
 </div>
</template>

<script>
var data = { a: 1 }

export default {
  data() {
    return {
      ChildJsonCalculData: data,
      forCount: [{'a':'1+1'},{'a':'1+1'},{'a':'1+1'},{'a':'1+1'},{'a':'1+1'},{'a':'1+1'},{'a':'1+1'},{'a':'1+1'},{'a':'1+1'},{'a':'1+1'}]
    }
  },
  props: {
    jsonCalculData: {
      type: Object,
      required: true,
      default: data
    }
  }
}
</script>

<style scoped>
.wrapper {
  max-width: 940px;
  margin: 0 auto;
}
.wrapper > div {
  border: 1px solid rgb(233,171,88);
  border-radius: 5px;
  background-color: rgba(255,255,255,.5);
  padding: 1em;
  color: #d9480f;
}.wrapper {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 10px;
  grid-auto-rows: minmax(190px, auto);
}

.span {
 color: #d9480f;
}
</style>
