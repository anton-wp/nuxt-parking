<template>
  <div>
    <moduleSVG />
    <Header />
    <Nuxt />
  </div>
</template>

<script>
import moduleSVG from "~/components/moduleSVG";
import Header from "~/components/Header"

export default {
  components: {
    moduleSVG,
    Header
  },
}
</script>

<style>
body{
  margin: 0;
  font-family: 'Roboto', sans-serif;
}

</style>
