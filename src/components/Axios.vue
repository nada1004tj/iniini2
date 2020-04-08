<template>
  <div class="div1">
    <button @click="fetchData">문제생성</button>&nbsp;&nbsp;
    <button @click="fetchData">답확인</button>
  </div>
</template>
<script>

export default {
  methods: {
    fetchData: function() {
        this.$axios.get('/api/users')
            .then((response) => {
                console.log(response.data);
                this.$emit("axiosData",response.data)
            })
    }
  }
}
</script>

<style scoped>
.div1{
  height:100px;
  margin-top:30px;
  text-align:center;
}

button{
  background:#1AAB8A;
  color:#fff;
  border:none;
  position:relative;
  height:60px;
  font-size:1.6em;
  padding:0 2em;
  cursor:pointer;
  transition:800ms ease all;
  outline:none;
  margin-top:20px;
}
button:hover{
  background:#fff;
  color:#1AAB8A;
}
button:before,button:after{
  content:'';
  position:absolute;
  top:0;
  right:0;
  height:2px;
  width:0;
  background: #1AAB8A;
  transition:400ms ease all;
}
button:after{
  right:inherit;
  top:inherit;
  left:0;
  bottom:0;
}
button:hover:before,button:hover:after{
  width:100%;
  transition:800ms ease all;
}
</style>
