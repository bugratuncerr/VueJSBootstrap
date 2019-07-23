//App.vue
<template>
  <div>
    <Navbar />
    <Shared />
    <br />
    <b-row id="new-group">
      <button class="btn btn-primary" @click="selectedComponent = 'cards'">
        Equal Payment Template
      </button>
      <button
        class="btn btn-primary"
        @click="selectedComponent = 'noPaymentPeriod'"
      >
        No Payment Period Template
      </button>
      <button
        class="btn btn-primary"
        @click="selectedComponent = 'balloonPayment'"
      >
        Balloon Payment Template
      </button>
      <button
        class="btn btn-primary"
        @click="selectedComponent = 'incDecPayment'"
      >
        Increase/Decrease Payment Template
      </button>
      <button
        class="btn btn-primary"
        @click="selectedComponent = 'flexiblePayment'"
      >
        Flexible Payment Template
      </button>
    </b-row>
    <hr />
    <component :is="selectedComponent">
      <p>This is the Content</p>
    </component>
    <Footer />
  </div>
</template>

<script>
import Cards from "./components/Cards.vue";
import Navbar from "./components/Navbar.vue";
import Shared from "./components/Shared.vue";
import Footer from "./components/Footer.vue";
import NoPaymentPeriod from "./components/NoPaymentPeriod.vue";
import BalloonPayment from "./components/BallonPayment.vue";
import IncDecPayment from "./components/IncDecPayment.vue";
import FlexiblePayment from "./components/FlexiblePayment.vue";
export default {
  data: function() {
    return {
      selectedComponent: "cards"
    };
  },
  components: {
    cards: Cards,
    noPaymentPeriod: NoPaymentPeriod,
    balloonPayment: BalloonPayment,
    incDecreasePayment: IncDecPayment,
    flexiblePayment: FlexiblePayment,
    Shared,
    Footer,
    Navbar
  }
};
</script>

<style>
#new-group {
  justify-content: center !important;
  background-color: white;
}
</style>
