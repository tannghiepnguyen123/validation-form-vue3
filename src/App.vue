<template>
  <div class="d-flex">
    <side-image />
    <donate-form />
  </div>
</template>

<script>
import DonateForm from './components/DonateForm.vue';
import SideImage from './components/SideImage.vue';
import AOS from 'aos'
import 'aos/dist/aos.css'

export default {
  name: "App",
  components: { DonateForm, SideImage },
  created() {
    AOS.init()
  }
}
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
