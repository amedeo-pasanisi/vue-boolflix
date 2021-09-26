<template>
  <div class="loader">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
      <path d="M18 13 L26 2 8 13 14 19 6 30 24 19 Z" />
    </svg>
    <div class="text">Loading...</div>
  </div>
</template>

<script>
export default {
  name: 'Loader'
}
</script>

<style scoped lang="scss">
.loader {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  svg {
      filter: invert(1);
      width: 70px;
      margin: 1rem 0;
      animation: pulse 1s infinite alternate
  }
  @keyframes pulse {
      from {
          transform: scale(1);
      }
      to {
          transform: scale(1.5);
      }
  }
  .text {
      color: white;
      font-weight: 600;
  }
}
</style>