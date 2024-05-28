<script>
export default{
    props: {
        fila: Number,
        columna: Number,
        Jugador1: Boolean,
        Jugador2: Boolean,
        MuroHori: Boolean,
        MuroVert: Boolean,
        
    },
    methods: {
        ClickCelda(){
            this.$emit('CeldaClickeada', {fila: this.fila, columna: this.columna});
        }, 
    },
};
</script>
<template>
    <div :class="['celda', {'J1': Jugador1, 'J2':Jugador2, 'Vmuro': MuroVert, 'Hmuro':MuroHori}]" @click="ClickCelda">
        </div>
        <div v-if="MuroHori && MuroVert" class="ContMuro">+</div>
        <div v-else-if="MuroHori" class="ContMuro">|</div>
        <div v-else-if="MuroVert" class="ContMuro">--</div>
        
</template>
<style>
.celda{
    width: 50px;
    height: 50px;
    border: 1px solid black;
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;   
}
.J1{
    background-color: pink;
}
.J2{
    background-color: purple;
}
.Hmuro::before {
  content: '';
  width: 100%;
  height: 5px;
  background-color: black;
  position: absolute;
  bottom: 0;
  left: 0;
}

.Vmuro::after {
  content: '';
  width: 5px;
  height: 100%;
  background-color: black;
  position: absolute;
  right: 0;
  top: 0;
}
.ContMuro{
    font-size: 12px;
    font-weight: bold;
    color: white;
}


</style>