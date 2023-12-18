<template>
  <div class="row" v-if="!!playersShown.length">
    <PlayersCard v-for="(player, i) in playersShown" :key="i" :player="player" />
  </div>
  <div class="error" v-else>please try adjusting your filter</div>
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
