<template>
  <div id="tab-bar">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "TaBBar",
};
</script>

<style>
#tab-bar {
  display: flex;
  background-color: #f6f6f6;
  border-top: 1px solid #eee;
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  box-shadow: 0px -3px 1px rgba(100, 100, 100, 0.1);
  z-index: 90;
}
</style>