<script lang="ts" setup>
const isVisibleSearch = ref(false)

// const props = defineProps<{
//   modelValue: boolean
// }>()
// const emits = defineEmits<{
//   (e: 'update:modelValue', isVisibleSearch: boolean): void
// }>()
// const visible = computed({
//   get: () => props.modelValue,
//   set: (val: boolean) => emits('update:modelValue', val),
// })

// const handleCloseSearch = () => {
//   emits('update:modelValue', false)
//   console.log(123)
// }
</script>

<template>
  <div class="header-search" @click="isVisibleSearch = true">
    <i class="icon-search"></i>
    <Teleport to="body">
      <div class="header-search-modal" v-if="isVisibleSearch">
        <div class="search-box">
          <!-- <i class="icon-close" @click="handleSearch"></i> -->
          <input type="text" placeholder="Input Keyword" />
        </div>
      </div>
    </Teleport>
  </div>
</template>

<style scoped lang="scss">
.header-search {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 30px;
  height: 30px;
  margin-left: 20px;
  cursor: pointer;

  .icon-search {
    position: relative;
    display: block;
    width: 13px;
    height: 13px;
    padding: 3px;
    border: 2px solid var(--nt-c-white-soft);
    border-radius: 50%;

    &::after {
      position: absolute;
      right: -6px;
      bottom: -2px;
      content: '';
      width: 8px;
      height: 2px;
      overflow: hidden;
      background-color: var(--nt-c-white-soft);
      transform: rotate(45deg);
    }
  }
}
.header-search-modal {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 99999;

  .search-box {
    position: fixed;
    width: 600px;
    height: auto;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    background-color: rgba(0, 0, 0, 0.6);
    border-radius: 6px;
    padding: 20px;

    input {
      border: none;
      background-color: rgba(0, 0, 0, 0.5);
      width: 100%;
      height: 34px;
      line-height: 34px;
      padding: 0 10px;
      border-radius: 4px;
      color: #999;
      font-size: 16px;
    }

    .icon-close {
      position: absolute;
      right: -15px;
      top: -15px;
      color: var(--nt-c-white-soft);
      font-size: 30px;
      font-style: normal;
      background-color: rgba(0, 0, 0, 0.7);
      width: 40px;
      height: 40px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;

      &::after {
        position: absolute;
        content: '';
        width: 18px;
        height: 2px;
        background-color: var(--nt-c-white-soft);
        transform: rotate(-45deg);
        opacity: 0.6;
      }

      &::before {
        position: absolute;
        content: '';
        width: 18px;
        height: 2px;
        background-color: var(--nt-c-white-soft);
        transform: rotate(45deg);
        opacity: 0.6;
      }

      &:hover {
        background-color: rgba(0, 0, 0, 0.7);
        &::after,
        &::before {
          opacity: 1;
        }
      }
    }
  }
}
</style>
