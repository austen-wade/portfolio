<template>
  <div class="section">
    <h2 class="title">{{ title }}</h2>
    <slot />
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: 'Section Title'
    }
  }
}
</script>

<style lang="scss">
[class^='section'] {
  padding: 40px 20px;

  @include _600 {
    padding: 40px 80px;
  }

  > .title {
    margin: 0 auto;
    font-weight: 200;
    color: $lightGray;
    text-align: center;
  }
}
</style>
