<script setup></script>

<template>
  <button class="button">
    <slot></slot>
  </button>
</template>

<style scoped>
.button {
  border-color: #000000;
  border-radius: 100px;
  background: var(--color-bg-btn);
  padding: 16px 10px;
  font-family: var(--font);
  font-size: 24px;
  font-weight: 400;
  line-height: 36px;
  color: var(--primary);
  cursor: pointer;
  width: 335px;
  height: 68px;
  box-shadow: 0px 4px 4px #00000040, 0px 4px 4px #00000040;
}
</style>
