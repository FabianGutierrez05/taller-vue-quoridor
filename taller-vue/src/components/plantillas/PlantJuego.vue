<template>
    <div class="PlantJ" @keydown="TeclasFlechas" tabindex="0">
        <MsgTurno :mensaje="msgTurno"/>
        <TabJuego :tablero="tablero" :jugadores="jugadores"  @CeldaClickeada="MnjClickCelda" />
        <ControlesMov :MurosActuales="MurosActuales" :ModoAccion="ModoAccion" @mover="MnjMov" @PonerMuro="MnjMuroPos" @reiniciar="reiniciarJuego" @cambiarModo="cambiarModoAccion" @MuroOrientacion="PonerOrientacion"/>

    </div>
</template>
<script>
import MsgTurno from '../organismos/MsgTurno.vue';
import TabJuego from '../organismos/TabJuego.vue';
import ControlesMov from '../moleculas/ControlesMov.vue';

export default{
    components: {MsgTurno, TabJuego, ControlesMov},
    data()  {
        return {
            tablero: this.IniciarTablero(),
            jugadores: [
                {id:1, fila:0, columna:4, Muros:10, MetaFila:8},
                {id:2, fila:8, columna:4, Muros:10, MetaFila:0}
            ],
            JugActual: 0,
            Ganador: null,
            msgTurno: 'Turno del jugador 1',
            ModoAccion: 'mover',
            OrientacionMuro: 'horizontal',
        };
    },
    computed: {
        
    },
    methods:{
        IniciarTablero(){
            const tablero = [];
            for (let i=0; i<9; i++){
                const fila = [];
                for(let j=0; j<9; j++){
                    fila.push({fila: i, columna: j, MuroHori: false, MuroVert: false });
                }
                tablero.push(fila);
            }
            return tablero;
        },
    }
}
</script>
<style>
    .PlantJ{
        display: flex;
  flex-direction: column;
  align-items: center;
    }
</style>