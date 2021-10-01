<template>
  <header class="container py-5">
    <h1 class="text-center">{{title}}</h1>
  </header>
</template>

<script>
export default {
	name: "Header",
  props: ['title']
}
</script>

<style lang="scss" scoped>
  h1 {
    font-weight: bold;
  }
</style>