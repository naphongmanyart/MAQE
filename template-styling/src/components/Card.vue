<template>
  <div class="card" :class="index % 2 != 0 ? 'blue-bg mt-3 mb-3' : ''">
    <div
      class="card-header d-flex align-items-center"
      :class="index % 2 !== 0 ? 'blue-bg' : ''"
    >
      <div class="avatar mr-2">
        <img class="img-avatar" :src="getAuthorAvatar(post.author_id)" alt="" />
      </div>
      <a class="custom-link" href="#"
        ><div class="author mr-2">{{ getAuthorName(post.author_id) }}</div></a
      >
      <div class="post-details">
        posted on {{ getHumanDate(post.created_at) }}
      </div>
    </div>
    <div class="card-body">
      <div class="d-flex">
        <div class="l-col mr-3">
          <img :src="post.image_url" alt="" />
        </div>
        <div class="r-col">
          <h5 class="card-title">{{ post.title }}</h5>
          <p class="card-text">{{ post.body }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import moment from 'moment';
export default {
  props: ['authors', 'post', 'index'],
  mounted() {
    console.log(this.authors);
  },
  methods: {
    getAuthorName(id) {
      let name = null;
      this.authors.forEach((author) => {
        if (author.id === id) {
          name = author.name;
        }
      });
      return name;
    },
    getAuthorAvatar(id) {
      let img = null;
      this.authors.forEach((author) => {
        if (author.id === id) {
          img = author.avatar_url;
        }
      });
      return img;
    },
    getHumanDate(date) {
      return moment(date, 'YYYY-MM-DD').format('dddd, MMMM D, YYYY, h:mm');
    },
  },
};
</script>

<style lang="scss" scoped>
.blue-bg {
  background-color: #c2e8ff !important;
}

.img-avatar {
  border-radius: 50%;
  width: 2.5rem;
  height: 2.5rem;
}

.custom-link {
  color: #f32c18;
}

.card-header {
  background-color: #fff;
}

.post-details {
  color: #9ea4ac;
}
</style>
