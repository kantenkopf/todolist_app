<template>
  <button class="btn border" @click="$emit('toggled'); toggleAcitive()">
    <i class="bi bi-list" v-if="!optionsActive" />
    <i class="bi bi-x" v-if="optionsActive" ></i>
  </button>
</template>

<script>
export default {
  data() {
    return {
      optionsActive: false,
    }
  },
  methods: {
    toggleAcitive() {
      this.optionsActive = !this.optionsActive;
    }
  }
}
</script>

<style>

</style>