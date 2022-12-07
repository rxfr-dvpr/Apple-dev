<template>
  <Nav/>
  
  <main class="main">

    <iPhone14Pro/>

    <iPhone14/>

    <AirpodsPro/>

    <section class="homepage__section">
      <div class="container">
        <div class="row">

          <WatchUltra/>

          <WatchSeries8/>

          <FitnessPlus/>

          <WatchSe/>

          <GiftCard/>

          <Card/>

        </div>
      </div> 
    </section>

    <AppleTvSlider/>
  </main>

  <Footer/>

  <Simulator/>
</template>

<script>
import AirpodsPro from './components/AirpodsPro.vue'
import AppleTvSlider from './components/AppleTvSlider.vue'
import Card from './components/Card.vue'
import FitnessPlus from './components/FitnessPlus.vue'
import Footer from './components/Footer.vue'
import GiftCard from './components/GiftCard.vue'
import iPhone14 from './components/iPhone14.vue'
import iPhone14Pro from './components/iPhone14Pro.vue'
import Nav from './components/Nav.vue'
import Simulator from './components/Simulator.vue'
import WatchSe from './components/WatchSe.vue'
import WatchSeries8 from './components/WatchSeries8.vue'
import WatchUltra from './components/WatchUltra.vue'


export default {
  name: 'App',
  components: {
    Nav,
    iPhone14,
    iPhone14Pro,
    AirpodsPro,
    WatchUltra,
    WatchSeries8,
    FitnessPlus,
    WatchSe,
    GiftCard,
    Card,
    AppleTvSlider,
    Footer,
    Simulator
  }
}
</script>

<style lang="scss" scoped>

.main {
  display: flex;
  flex-direction: column;
  row-gap: 12px;

  .homepage__section {
    width: 100%;

    & > .container {
      max-width: 2535px !important;

      & > .row {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        gap: 12px;
      }
    }
  }
}

@media (max-width: 736px) {
  .homepage__section {
    .container {
      padding: 0 !important;
    }

    .row {
      grid-template-columns: repeat(1, 1fr) !important;
    }
  }
}

</style>
