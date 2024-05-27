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
        MurosActuales(){
            return this.jugadores[this.JugActual].Muros;
        },
    },
        mounted() { //sin este metodo los atajos de teclado no funcionan
        this.$el.focus();
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
        MnjMov(direccion){
            if (this.ModoAccion!='mover') return;

            const jugador=this.jugadores[this.JugActual];
            let nuevaFila = jugador.fila;
            let nuevaCol = jugador.columna;

            switch(direccion){
                case 'up' :
                    nuevaFila -= 1;
                    break;
                case 'down':
                    nuevaFila += 1;
                    break;
                case 'left':
                    nuevaCol -= 1;
                    break;
                case 'right':
                    nuevaCol += 1;
                    break;
            }
            if(this.MovValido(jugador, nuevaFila, nuevaCol)){       
                jugador.fila=nuevaFila;
                jugador.columna=nuevaCol;
                if(this.VerifGanador(jugador)){
                    this.Ganador= jugador.id;
                    this.msgTurno = `¡El jugador ${jugador.id} ha ganado!`;
                }else {
                    this.cambiarJug();
                }
            }else{
                alert('Movimiento no valido');
            }
            },
            MnjMuroPos(){
                this.ModoAccion= 'muro';
            },
            MovValido(jugador, fila, columna){
                const filaDif = Math.abs(jugador.fila - fila);
                const ColDif = Math.abs(jugador.columna - columna);
                if (filaDif + ColDif !==1) return false;

                for(const otroJug of this.jugadores){
                    if (otroJug !== jugador && otroJug.fila === fila && otroJug.columna === columna){
                        return false;
                    }
                }
                if(filaDif===1){
                    if (jugador.fila < fila && this.tablero[jugador.fila][jugador.columna].MuroHori) return false;
                    if (jugador.fila > fila && this.tablero[fila][columna].MuroHori) return false;
                }
                if(ColDif === 1){
                    if (jugador.columna < columna && this.tablero[jugador.fila][jugador.columna].MuroVert)return false;
                    if (jugador.columna > columna && this.tablero[fila][columna].MuroVert) return false;
                }
                return fila >=0 && fila < 9 && columna >=0 && columna <9;
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