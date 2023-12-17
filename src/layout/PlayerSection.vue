<template>
  <div class="player-section">
    <WebLoader v-if="isLoading" />
    <div v-else class="container">
      <SearchAndFilter
        :skills="skills"
        :selected="selected"
        :search="search"
        @changeOption="changeOption"
        @changeSearch="changeSearch"
      />
      <PlayerList :playersShown="playersShown" />
    </div>
  </div>
</template>
<script>
import PlayerList from '../components/PlayerList.vue'
import WebLoader from '../components/WebLoader.vue'
import SearchAndFilter from '../components/SearchAndFilter.vue'
import { fetchData } from '../api/fetchData.js'
export default {
  data() {
    return {
      players: [],
      search: '',
      skills: [],
      isLoading: false,
      selected: 'All'
    }
  },
  computed: {
    playersShown() {
      let { players, selected, search } = this
      if (selected !== 'All') {
        players = players.filter((player) => player.skill == selected)
      }
      if (search) {
        const searchLower = search.toLowerCase()
        players = players.filter((player) => player.player_name.toLowerCase().includes(searchLower))
      }
      return players
    }
  },
  async created() {
    this.isLoading = true
    try {
      let players = await fetchData('/players.json')
      this.players = players.players
      this.skills = ['All', ...new Set(players.players.map((player) => player.skill))]
    } catch (e) {
      console.error(e)
    } finally {
      this.isLoading = false
    }
  },
  methods: {
    changeOption(id) {
      this.selected = id
    },
    changeSearch(val) {
      console.log(val)
      this.search = val
    }
  },
  components: {
    PlayerList,
    WebLoader,
    SearchAndFilter
  }
}
</script>
