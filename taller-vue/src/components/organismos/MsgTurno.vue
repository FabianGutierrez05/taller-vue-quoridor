<script>
   export default{
    props: {
        mensaje: String,
    },
   } ;
</script>
<template>
    <div class="msj">{{mensaje}}</div>
</template>
<style>
.msj{
    background-color: #bf8e2c;
  color: #fff;
  border-radius: 10%;
  border: #88E8F2;  
}
</style>