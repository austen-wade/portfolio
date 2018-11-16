<template>
  <a
    :href="href"
    :target="targetBlank ? '_blank' : ''"
    class="btn menu-btn">
    <span class="btn-text">{{ text }}</span>
  </a>
</template>

<script>
export default {
  props: {
    href: {
      type: String,
      default: '#'
    },
    text: {
      type: String,
      default: 'Link'
    },
    targetBlank: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss">
.menu-btn {
  display: block;
  position: relative;
  border: 1px solid $black;
  color: $black;
  padding: 15px;
  width: 200px;
  transition: color 500ms;
  text-align: center;
  text-decoration: none;
  overflow: hidden;

  > .btn-text {
    position: relative;
    z-index: 2;
  }

  & + .menu-btn {
    margin-top: 10px;
  }
  &:before {
    content: '';
    position: absolute;
    background-color: $black;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    transform: translateX(-100%);
    transition: transform 500ms;
  }

  &:hover {
    color: $white;

    &:before {
      transform: translateX(0%);
    }
  }
}
</style>
