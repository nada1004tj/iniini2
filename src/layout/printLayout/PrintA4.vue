<template>
  <div size="A4" id="printLayer">
    123123
  </div>
</template>

<script>
</script>

<style scoped>
/* 로컬 스타일 */
div {
background: white;
display: block;
margin: 0 auto;
margin-bottom: 0.5cm;
box-shadow: 0 0 0.5cm rgba(0,0,0,0.5);
}
div[size="A4"] {
width: 21cm;
height: 29.7cm;
}

@media print {
body, div {
  margin: 0;
  box-shadow: 0;
}
}
</style>
