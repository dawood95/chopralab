<template>
  <div>
  <footer class="w-full pin-b border-grey">
    <ul class="flex items-center justify-end text-base pt-4 lg:pt-0 lg:mb-0 mb-2">
      <li v-for="menu_item in menu">
        <g-link
          class="px-4 py-3 text-sm inline-block hover:text-gray-700 border-b-2 border-transparent"
          exact-active-class="border-gray-600"
          :to="menu_item.link">
          {{menu_item.name}}
        </g-link>
      </li>
    </ul>
  </footer>
  </div>
</template>

<script>
export default {
  data () { return {
    menu: [
      {name: 'twitter', link: '#'},
      {name: 'github', link: '#'},
    ],
  }},
};
</script>

<style>

</style>
