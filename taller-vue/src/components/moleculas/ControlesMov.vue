<script>
export default{
    props:{
        MurosActuales: Number,
        ModoAccion: String
    }
};
</script>

<template>
    <div class="ControlMov">
        <button @click="$emit('ActivModoAccion')">{{ ModoAccion === 'mover' ? 'Cambiar a Poner  Muro' : 'Cambiar a Moverse'}}</button>
        <div v-if="ModoAccion === 'muro'">
            <button @click="$emit('PonerMuro')">Poner Muro</button>
            <p>Selecciona la orientacion del muro:</p>
            <button @click="$emit('setOrientacionMuro', 'horizontal')">Horizontal</button>
            <button @click="$emit('setOrientacionMuro', 'vertical')">Vertical</button>
            <p>Muros restantes: {{ MurosActuales }}</p>
        </div>
    </div>
</template>

<style scoped>
.ControlMov {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>