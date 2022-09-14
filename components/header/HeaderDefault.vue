<script lang="ts" setup>
const isScroll = ref(false)
onMounted(() => {
  window.addEventListener('scroll', () => {
    const scrollTop =
      window.pageYOffset ||
      document.documentElement.scrollTop ||
      document.body.scrollTop

    scrollTop > 10 ? (isScroll.value = true) : (isScroll.value = false)
  })
})
</script>

<template>
  <div class="header" :class="{ 'header-fixed': isScroll }">
    <h1 class="logo">Nuxt Theme Less</h1>
    <HeaderMenu />
    <HeaderSearch />
  </div>
</template>

<style scoped lang="scss">
.header {
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  height: var(--nt-header-height-desktop);
  padding: 0 100px;
  background-color: transparent;
  color: var(--nt-c-white-soft);
  z-index: 9999;

  .logo {
    font-size: 20px;
    font-weight: normal;
  }
}

.header-fixed {
  position: fixed;
  background-color: #333;
  height: 100px;
  box-shadow: 0 0 8px 1px rgb(0 0 0 / 20%);
  animation: fadeInDown 0.9s cubic-bezier(0.2, 1, 0.22, 1) 0s 1 normal none
    running;
}
</style>
