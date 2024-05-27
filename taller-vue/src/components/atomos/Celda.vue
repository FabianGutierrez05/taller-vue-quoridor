<script>
export default{
    props: {
        fila: Number,
        Columna: Number,
        Jugador1: Boolean,
        Jugador2: Boolean,
        MuroVert: Boolean,
        MuroHori: Boolean,
    },
    methods: {
        ClickCelda(){
            this.$emit('CeldaClickeada', {fila: this.fila, Columna: this.Columna});
        }, 
    },
};
</script>
<template>
    <div :class="['celda', {'J1': Jugador1, 'J2':Jugador2, 'Vmuro': MuroVert, 'Hmuro':MuroHori}]" @click="ClickCelda">
        </div>
        <div v-if="MuroVert && MuroHori" class="ContMuro">+</div>
        <div v-else-if="MuroVert" class="ContMuro">--</div>
        <div v-else-if="MuroHori" class="ContMuro">|</div>
</template>
<style>
.celda{
    width: 50px;
    height: 50px;
    border: 3px solid black;
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
.ContMuro{
    font-size: 12px;
    font-weight: bold;
    color: white;
}


</style>