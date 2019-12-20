<template>
  <div class="container">
    <article>
      <h1 class="title">{{ post.title }}</h1>
      <p>{{ post.content }}</p>
    </article>
    <aside>
      <h3>Posts you might enjoy</h3>
      <ul>
        <li v-for="related in relatedPosts" :key="related.id">
          <nuxt-link :to="{ name: 'posts-id', params: { id: related.id } }">
            {{ related.title }}
          </nuxt-link>
        </li>
      </ul>
    </aside>
  </div>
</template>

<script>
export default {
  data() {
    return {
      id: this.$route.params.id,
      posts: [
        {
          id: "balut",
          title: "What is Balut?",
          content:
            "If someone placed balut on your plate, you might think they were serving you a hardboiled egg. That is, until you cracked it open and a fully intact duck embryo spilled out. Balut, considered a delicacy in many Asian countries, is produced when fertilized duck eggs are placed in warm sunlight. After about eight days, the eggs are held up to the light and checked to ensure that the budding embryo is ready. Then, the eggs are cooked and served with a dash of salt and a few squirts of lemon juice."
        },
        {
          id: "whereIsIt",
          title: "Where is the sign in button?",
          content: "Sign Button blablabla."
        },
        {
          id: "how",
          title: "How can I fix this problem?",
          content: "Fix my problem blablabla"
        }
      ]
    };
  },
  computed: {
    post() {
      return this.posts.find(post => post.id === this.id);
    },
    relatedPosts() {
      return this.posts.filter(post => post.id !== this.id);
    }
  }
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: space-between;
  line-height: 1.5;
}
article * {
  margin-bottom: 1rem;
}
aside {
  min-width: 280px;
  max-width: 280px;
  padding-left: 2rem;
}
.title {
  font-size: 2rem;
}
</style>
