<script setup lang="ts">
import Side from "./components/Side.vue"
import Content from "./components/Content.vue";
</script>

<template>
  <header>
    <div class="grid-container">
      <Side/>
      <Content/>
    </div>
  </header>
</template>

<style scoped>
header {
  line-height: 1.5;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
  }

  header .wrapper {
    width: 100%;
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;
    padding: 1rem 0;
    margin-top: 1rem;
  }
}

.grid-container {
  width: 100%;
  display: grid;
  grid-template-columns: 1fr 3fr;
  grid-template-rows: 1fr max-content;
}

.grid-container>div {
  text-align: center;
  font-size: 30px;
  margin: 10px;
}
</style>
