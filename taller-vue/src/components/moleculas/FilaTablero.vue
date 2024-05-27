<script>
    import Celda from '../atomos/Celda.vue';

    export default {
        props: {
            fila: Array,
            jugadores: Array
        },
        components: {Celda},
        methods: {
            PosJ1(fila, columna) {
                const J1 = this.jugadores[0];
                return J1.fila === fila && J1.columna === columna;
            },
            PosJ2(fila, columna) {
                const J2 = this.jugadores[1];
                return J2.fila === fila && J2.columna === columna;
            },
            MnjClickCelda({fila, columna}) {
                this.$emit('CeldaClickeada', {fila: this.fila, columna: this.columna})
            },
        },
    };
</script>

<template>
    <div class="filaTablero">
        <Celda
        v-for="celda in fila"
        :key="celda.columna"
        :fila="celda.fila"
        :columna="celda.columna"
        :Jugador1="Jugador1(celda.fila, celda.columna)"
        :Jugador2="Jugador2(celda.fila, celda.columna)"
        :MuroVert="celda.MuroVert"
        :MuroHori="celda.MuroHori"
        @cellClicked="handleCellClick"
        />
    </div>
</template>

<style scoped>
.filaTablero {
  display: flex;
}
</style>