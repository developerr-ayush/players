<template>
  <div class="row">
    <div class="col-lg-6">
      <DropDown v-if="skills" :skills="skills" :selected="selected" @changeOption="changeOption" />
    </div>
    <div class="col-lg-6">
      <FormInput
        type="search"
        placeholder="Search Players"
        :value="search"
        @changeSearch="changeSearch"
      />
    </div>
  </div>
</template>

<script>
import DropDown from './DropDown.vue'
import FormInput from './FormInput.vue'

export default {
  props: {
    skills: Array,
    selected: String,
    search: String
  },
  methods: {
    changeOption(id) {
      this.$emit('changeOption', id)
    },
    changeSearch(val) {
      console.log(val)
      this.$emit('changeSearch', val)
    }
  },
  components: {
    DropDown,
    FormInput
  }
}
</script>
