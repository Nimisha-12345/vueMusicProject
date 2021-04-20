<template>
  <div id="app">
    <HeadSection />
    <Music />
  </div>
</template>

<script>
import HeadSection from './components/HeadSection'
import Music from './components/Music'

export default {
  name: "App",
  components: {
    HeadSection,
    Music

  },
};
</script>

