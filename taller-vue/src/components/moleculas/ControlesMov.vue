<script>
import Boton from '../atomos/Boton.vue';
export default{
    props:{
        MurosActuales: Number,
        ModoAccion: String
    }
};
</script>

<template>
    <div class="ControlMov">
        <Boton @click="$emit('reiniciar')" class="btn-primario">Reiniciar</Boton>
        <Boton @click="$emit('ActivModoAccion')" class="btn-primario">{{ ModoAccion === 'mover' ? 'Cambiar a Poner  Muro' : 'Cambiar a Moverse'}}</Boton>
        <div v-if="ModoAccion === 'mover'"></div>
        <div v-if="ModoAccion === 'muro'">
            <p>Selecciona la orientacion del muro:</p>
            <Boton @click="$emit('setOrientacionMuro', 'horizontal    ')" class="btn-primario">Horizontal</Boton>
            <Boton @click="$emit('setOrientacionMuro', 'vertical')" class="btn-primario">Vertical</Boton>
            <p>Muros restantes: {{ MurosActuales }}</p>
        </div>
    </div>
</template>

<style scoped>
p{
    background-color: #bf8e2c;
  color: #fff;
  border-radius: 10%;
  border: #88E8F2;  
}
.ControlMov {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #F29544;
}
.btn{
    display: flex;
    justify-content: center;
  align-items: center;
  padding: 20px;
  min-width: 200px;
  font-size: 30px;
  height: 30px;
  border-radius: 15px;
  cursor: pointer;
  box-shadow: 0px 0px 5px 5px rgb(0, 0, 0/28%);
  
}
.btn-primario{
  background-color: #BF2C2C;
  color: #fff;
  border-radius: 10%;
  border: #88E8F2;
}
.btn-primario:hover{
    background-color: #6BB3F2;
    color: #fff;
  }

</style>