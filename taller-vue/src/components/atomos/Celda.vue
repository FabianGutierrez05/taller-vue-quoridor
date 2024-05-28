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
    <div :class="['celda', {'celda-J1': Jugador1, 'celda-J2':Jugador2, 'Vmuro': MuroVert, 'Hmuro':MuroHori}]" @click="ClickCelda">
        </div>
        <div v-if="MuroHori && MuroVert" class="ContMuro">+</div>
        <div v-else-if="MuroHori" class="ContMuro">|</div>
        <div v-else-if="MuroVert" class="ContMuro">--</div>
        
</template>
<style>
.celda{
    width: 50px;
    height: 50px;
    border: 1px solid rgb(255, 235, 235);
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;   
}
.celda-J1{
    background-color: rgb(117, 17, 124);
    border-radius: 20%;
}
.celda-J2{
    background-color: rgb(20, 159, 169);
    border-radius: 20%;
}
.Hmuro::before {
  content: '';
  width: 100%;
  height: 5px;
  background-color: rgb(184, 141, 255);
  position: absolute;
  bottom: 0;
  left: 0;
}

.Vmuro::after {
    content: '';
    width: 5px;
    height: 100%;
    background-color:rgb(184, 141, 255);
    position: absolute;
    right: 0;
    top: 0;
}
.ContMuro{
    font-size: 0px;
    font-weight: bold;
    color: white;
}


</style>