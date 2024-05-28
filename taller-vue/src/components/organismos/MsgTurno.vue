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
    margin-bottom: 10px;
    font-size: 1.2em;
    background-color: #BF2C2C;
    border: 10px;
    color: #fff;
    border-color: #23518C;
    border-radius: 10%;
}
</style>