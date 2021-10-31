<template>
  <v-menu
    v-model="showDataMenu"
    :close-on-content-click="false"
    transition="scale-transition"
    offset-y
    min-width="auto"
  >
    <template v-slot:activator="{ on, attrs }">
      <v-text-field
        v-model="date"
        label="Date Picker"
        prepend-icon="mdi-calendar"
        clearable
        readonly
        v-bind="attrs"
        v-on="on"
        @click:clear="$emit('input', '')"
      />
    </template>
    <v-date-picker
      v-model="date"
      @input="showDataMenu = false"
      @change="change"
    />
  </v-menu>
</template>

<script>
export default {
  data () {
    return {
      date: '',
      showDataMenu: false
    }
  },
  methods: {
    change (date) {
      this.$emit('input', date)
    }
  }
}
</script>