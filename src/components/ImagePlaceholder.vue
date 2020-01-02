<template>
  <div class="loading">
    <div class="loading-anim" />
  </div>
</template>

<style scoped>
.loading {
  width: 400px;
  height: 400px;
  background-color: rgb(233, 233, 233);
}

.loading-anim {
  --colorBackground: #ffffff00;
  --colorHighlight: #949494;
  height: 400px;
  width: 400px;
  background: linear-gradient(
    to right,
    var(--colorBackground),
    var(--colorBackground),
    var(--colorHighlight),
    var(--colorBackground),
    var(--colorBackground)
  );
  background-size: 800% 100%;
  animation: 2s linear 0s infinite normal nowloading;
  mask-position: center;
}

@keyframes nowloading {
  0% {
    background-position: 100% 100%;
  }

  50% {
    background-position: 50% 100%;
  }

  100% {
    background-position: 0% 100%;
  }
}
</style>