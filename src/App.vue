<template>
  <div id='app'>
    <Navbar/>
    <Hero class="element"/>
    <main>
      <!-- <Diagrams class="element"/> -->
      <Articles class="element"/>
      <Quiz class="element"/>
      <Charity class="element"/>
    </main>
    <Footer class="element"/>
  </div>
</template>


<script>
import Navbar from '@/components/Navbar.vue'
import Hero from '@/components/Hero.vue'
// import Diagrams from '@/components/Diagrams.vue'
import Articles from '@/components/Articles.vue'
import Quiz from '@/components/Quiz.vue'
import Charity from '@/components/Charity.vue'
import Footer from '@/components/Footer.vue'

export default {
  name: 'App',
  components: {
    Navbar,
    Hero,
    // Diagrams,
    Articles,
    Quiz,
    Charity,
    Footer,
  }
}
</script>


<style lang="scss">
@import '@/assets/style/properties';
// $yellow;
// $light-green;
// $green;
// $dark-green;

// $padding-main;

html {
  scroll-behavior: smooth;
}

body {
  margin: 0;
  min-height: 100vh;
  overflow-x: hidden;
  background: $yellow;
}
* {
  box-sizing: border-box;
  margin: 0;
  font-family: 'Roboto';
}

#app {
  width: 100vw;
  .element {
    width: 100vw;
    min-height: 25vw;
  }
}
</style>
