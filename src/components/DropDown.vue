<template>
  <div class="dropdown">
    <button
      class="btn btn-secondary dropdown-toggle"
      type="button"
      data-bs-toggle="dropdown"
      aria-expanded="false"
    >
      {{ selected }}
    </button>
    <ul class="dropdown-menu">
      <li v-for="(skill, id) in skills" :key="id">
        <button @click="change(skill)" v-if="skill == selected" class="dropdown-item active">
          {{ skill }}
        </button>
        <button @click="change(skill)" v-else class="dropdown-item">{{ skill }}</button>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  props: {
    skills: {
      type: Array,
      required: true
    },
    selected: {
      type: String,
      required: true
    }
  },
  methods: {
    change(skill) {
      this.$emit('changeOption', skill)
    }
  }
}
</script>
