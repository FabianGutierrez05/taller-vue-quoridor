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
}
</style>