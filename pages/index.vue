<template>
  <div>
    <Navbar/>
    <div class="container">
      <button
        class="button"
        v-if="!showRivers"
        @click="showRivers = !showRivers"
      >
        Discover the rivers
      </button>
      <template v-if="showRivers">
        <Rivers/>
      </template>
    </div>
  </div>
</template>

<script>
import Navbar from '../components/Navbar';
import Rivers from '../components/Rivers';
export default {
  name: 'index',
  components: { Navbar, Rivers },
  data() {
    return {
      showRivers: false
    };
  },
};
</script>
