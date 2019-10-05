<template>
  <nav class="navbar flex items-center justify-between flex-wrap py-2 pb-10">
  <g-link class="inline-block font-logo text-4xl text-gray-900 tracking-tight" to='/'>CHOPRA LAB</g-link>
  <input class="hidden" type="checkbox" id="menu-toggle" />
  <label id="burger" for="menu-toggle" class="pointer-cursor text-gray-900 lg:hidden block p-2">
    <svg class="fill-current" xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 20 20">
      <title>menu</title><path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"></path>
    </svg>
  </label>

  <div class="hidden uppercase lg:flex lg:items-center lg:w-auto w-full" id="menu">
    <ul class="lg:flex items-center justify-between text-base pt-4 lg:pt-0 lg:mb-0 mb-2">
      <li v-for="menu_item in menu">
        <g-link
          class="lg:p-4 text-sm py-3 pl-2 inline-block hover:text-gray-700 border-b-2 border-transparent"
          exact-active-class="border-gray-600"
          :to="menu_item.link">
          {{menu_item.name}}
        </g-link>
      </li>
    </ul>
  </div>
</nav>
</template>

<script>
export default {
  data () { return {
    menu: [
      {name: 'news', link: 'news'},
      {name: 'publications', link: 'publications'},
      {name: 'software', link: '#'},
      {name: 'people', link: '#'},
      {name: 'contact', link: '#'},
      {name: 'join us', link: '#'},
    ],
  }},

  computed: {
    page() {
      return this.$route.path;
    }
  }
};
</script>

<style>
#menu-toggle:checked ~ #burger {
  @apply text-gray-200 bg-gray-800;
}
#menu-toggle:checked ~ #menu {
  @apply block;
}
</style>
