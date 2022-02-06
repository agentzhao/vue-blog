<template>
  <div v-if="error">{{ error }}</div>
  <div v-if="post" class="post">
    <h1>{{ post.title }}</h1>
    <p class="pre">{{ post.body }}</p>
  </div>
  <div v-else><Spinner /></div>
</template>

<script>
import getPost from "../composables/getPost";
import Spinner from "../components/Spinner";
import { useRoute } from "vue-router";

export default {
  props: ["id"],
  components: { Spinner },
  setup(props) {
    const route = useRoute();

    // can be getPost(props.id) or route.props.id
    const { post, error, load } = getPost(route.props.id);
    load();

    return {
      post,
      error,
    };
  },
};
</script>

<style>
.post {
  margin: 0 auto;
  max-width: 1200px;
}
.post p {
  color: #444;
  line-height: 1.5em;
  margin-top: 40px;
}
.pre {
  white-space: pre-wrap;
}
</style>
