<template>
  <button class="btn btn-secondary"
    @click="$emit('enableEdit')"
  >
      <i class="bi bi-pencil-fill"></i>
  </button>
</template>

<script>
export default {
  emits:['enableEdit']
}
</script>

<style>

</style>