<template>
  <div class="card">
    <slot></slot>
  </div>
</template>

<style scoped>
.card {
  background: white;
  padding: 20px;
  border-radius: 5px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px,
    rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
  overflow: hidden;
}
</style>
