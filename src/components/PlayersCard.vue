<template>
  <div class="col-lg-4 col-md-6 col-12">
    
    <div class="card">
      <img :src="player.image_url" class="card-img-top" :alt="player.player_name + ` image`" />
      <div class="card-body">
        <h5 class="card-title">{{ player.player_name }}</h5>
        <p>{{ player.skill }}</p>
        <p>{{ player.team_name }}</p>
        <p>
          <b>Upcoming Matches</b>
        </p>
        <ul>
          <li v-for="match in player.upcoming_matches" :key="match">
            <p>
              {{ match.match_name }}
            </p>
            <p>
              {{ new Date(match.match_date).getDate() }}
              {{ months[new Date(match.match_date).getMonth()] }},
              {{ new Date(match.match_date).getFullYear() }}
              |
              {{ new Date(match.match_date).getHours() }}:
              {{ new Date(match.match_date).getMinutes() }}
            </p>
          </li>
        </ul>
        <a href="#" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    player: {
      type: Object,
      required: true
    }
  },
  data: function () {
    return {
      months: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sept', 'Oct', 'Nov', 'Dec']
    }
  }
}
</script>
