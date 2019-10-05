<template>
  <div class="min-h-screen flex flex-col container mx-auto">
    <Navbar/>
    <div class="flex-1 mt-6">
      <slot/>
    </div>
    <Footer/>
  </div>
</template>

<script>
import Navbar from '~/components/Navbar.vue';
import Footer from '~/components/Footer.vue';


export default {
  components: {
    Navbar,
    Footer
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Oswald:400,500,700');
@import url('https://fonts.googleapis.com/css?family=Sintony:400,700');

html {
  @apply font-body font-normal;
}

</style>
