<template>
  <div id="app">
    <div class="container">
      <div class="content py-5">
        <h3 class="mb-5">MAQE Forum</h3>
        <p>Your current timezone is: Asia/Bangkok</p>
        <div class="card-container">
          <Card
            v-for="(post, index) in posts"
            :key="post.id"
            :index="index"
            :authors="authors"
            :post="post"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import authorsData from './json/authors.json';
import postsData from './json/posts.json';
import Card from './components/Card.vue';

export default {
  name: 'App',
  components: {
    Card,
  },
  data() {
    return {
      authors: authorsData,
      posts: postsData,
    };
  },
};
</script>

<style lang="scss">
html,
#app {
  background-color: #eaeaea;
}

h3 {
  font-weight: bold;
}
</style>
