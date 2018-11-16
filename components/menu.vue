<template>
  <div
    :class="menuActive ? '-active' : ''"
    class="menu">
    <div class="menu-btns">
      <MenuLink
        href="https://www.google.com"
        text="Google" />
      <MenuLink />
      <MenuLink />
      <MenuLink />
    </div>
  </div>
</template>

<script>
import MenuLink from './menu-link.vue'

export default {
  components: {
    MenuLink: MenuLink
  },
  props: {
    menuActive: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss">
.menu {
  height: 100vh;
  padding: 20px;
  width: 100%;
  background-color: $white;
  position: absolute;
  opacity: 0;
  pointer-events: none;
  transform: translateY(-20%);
  transition: opacity 1s, transform 1s;

  > .menu-btns {
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  &.-active {
    opacity: 1;
    pointer-events: all;
    transform: translateY(0%);
  }
}
</style>
