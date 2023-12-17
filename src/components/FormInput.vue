<template>
  <div class="input-group mb-3">
    <input
      :type="type"
      class="form-control"
      :placeholder="placeholder"
      aria-label="placeholder"
      :value="value"
      @input="updateSearch"
    />
  </div>
</template>
<script>
export default {
  props: {
    value: {
      type: String,
      required: true
    },
    type: {
      type: String,
      required: true
    },
    placeholder: {
      type: String,
      required: true
    }
  },
  methods: {
    updateSearch(event) {
      this.$emit('changeSearch', event.target.value)
    }
  }
}
</script>
