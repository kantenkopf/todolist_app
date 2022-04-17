<template>
  <button class="btn btn-secondary">
      <i class="bi" 
        :class="{ 'bi-caret-up-fill': direction === 1, 
                  'bi-caret-down-fill': direction === -1}"
      />
  </button>
</template>

<script>

export default {
    props:['direction']
}
</script>

<style>
</style>