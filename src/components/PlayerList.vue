<template>
  <div class="row">
    <PlayersCard v-for="(player, i) in playersShown" :key="i" :player="player" />
  </div>
</template>
<script>
import PlayersCard from '../components/PlayersCard.vue'
export default {
  props: {
    playersShown: Array
  },
  components: {
    PlayersCard
  }
}
</script>
