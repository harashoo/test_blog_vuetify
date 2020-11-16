<template>
  <v-card flat>
    <v-img height="400" :src="article.image.url"></v-img>

    <v-card-title>{{ article.title }}</v-card-title>

    <v-card-text>
      <div>{{ article.body }}</div>
    </v-card-text>
  </v-card>
</template>

<script>
import axios from "axios";

export default {
  name: "ArticleDetail",

  data: () => ({
    article: {}
  }),

  async mounted() {
    const response = await axios.get(
      "https://my-blog-harasho.microcms.io/api/v1/articles/" +
        this.$route.params.id,
      {
        headers: { "X-API-KEY": process.env.VUE_APP_X_API_KEY }
      }
    );
    this.article = response.data;
  }
};
</script>
