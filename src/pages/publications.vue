<template>
<Layout>
  <div class="container">
    <p class="block text-xl mb-4 px-2">Publications</p>
    <ul>
      <li v-for="posts in groupedPosts">
        <p class="block text-xl font-semibold uppercase my-4 px-2">{{posts.year}}</p>
        <div class="overflow-hidden border border-gray-200 flex mb-2 shadow-md">
          <g-image :src="posts.node.image" class="flex-initial w-40 h-40 p-2"/>
          <div class="flex-auto px-6 py-4">
            <p class="text-sm text-gray-600 ">{{posts.node.date}}</p>
            <p class="text-lg text-gray-900 tracking-tight mb-2">{{posts.node.title}}</p>
            <p class="text-base text-gray-700">{{posts.node.content}}</p>
          </div>
        </div>
      </li>
    </ul>
    <div class="flex justify-end">
      <Pager :info="$page.posts.pageInfo" linkClass="inline-block font-bold py-3 px-4 items-center hover:bg-gray-800 hover:text-white"/>
    </div>
  </div>
</Layout>
</template>

<page-query>
query NewsPosts($page: Int) {
  posts: allNewsPosts(perPage: 7, page: $page, sortBy: "date", order:ASC) @paginate {
    pageInfo {
      totalPages
      currentPage
      isFirst
      isLast
    }
    edges {
      node {
        title
        date
        image (quality: 100)
        content
      }
    }
  }
}
</page-query>

<script>
import { Pager } from 'gridsome'

export default {
  components: {
    Pager
  },
  computed: {
    groupedPosts: function() {
      const posts = [];
      var prev_year = null;
      for (var p in this.$page.posts.edges) {
        var node = this.$page.posts.edges[p].node;
        var year = node.date.slice(-4);
        console.log(prev_year, year);
        if (prev_year === year) {
          year = null;
        }
        //console.log(p);
        //if (!posts.hasOwnProperty(year)) {
        //  posts[year] = [];
        //}
        posts.push({
          year, node
        });
        prev_year = year;
      }
      return posts;
    }
  }
}
</script>
