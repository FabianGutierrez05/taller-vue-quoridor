<template>
  <div class="pagina-juego">
    <GameTemplate/>
  </div>
</template>
<script>
import GameTemplate from '../components/plantillas/GameTemplate.vue';

export default {
  components: {GameTemplate},
};
</script>

<style scoped>
.game-page{
  padding: 20px;
}
</style>