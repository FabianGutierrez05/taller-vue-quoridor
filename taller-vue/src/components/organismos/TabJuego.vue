<script>
import FilaTablero from '../moleculas/FilaTablero.vue';
export default {
    props:{
        tablero: Array,
        jugadores: Array,
    },
    components: {FilaTablero},
    methods: {
        MnjClickCelda({fila, columna}) {
                this.$emit('CeldaClickeada', {fila, columna})
            },
},
};
</script>

<template>
    <div class="Tablero">
      <FilaTablero
        v-for="(fila, filaIndex) in tablero"
        :key="filaIndex"
        :fila="fila"
        :jugadores="jugadores"
        @CeldaClickeada="MnjClickCelda"/>
    </div>
  </template>

<style>
.Tablero{
    display: flex;
    flex-direction: column;
    
}
</style>