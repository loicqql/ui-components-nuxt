<template>
  <div class="index">
    <NuxtLink to="/road-96">Road-96</NuxtLink>
    <NuxtLink to="/cyberpunk-2077">Cyberpunk 2077</NuxtLink>
  </div>
</template>

<style lang="scss" scoped>
.index {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-flow: column nowrap;
  height: 100vh;
  a {
    padding: 0.2rem;
    font-family: "Inter", sans-serif;
    color: #000;
    text-decoration: none;
  }
}
</style>