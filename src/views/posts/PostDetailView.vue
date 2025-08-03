<template>
  <div>
    <h2>게시글 상세</h2>
     <h4 class="my-4"></h4>
     <p> params: {{ $route.params }}</p>
     <p> query: {{ $route.query.searchText }}</p>
     <p> query: {{ $route.hash }}</p>
  </div>
</template>

<script setup>

</script>

<style lang="scss" scoped>

</style>