<template>
  <div class="container column">
    <app-form @addBlock="newBlock"></app-form>
    <app-resume :blocks="blocks"></app-resume>
  </div>
  <app-loader v-if="loading"></app-loader>
  <app-comments
    v-else
    :comments="comments"
    @load-comments="loadComments"
  ></app-comments>
</template>

<script>
import AppResume from "./AppResume.vue";
import AppForm from "./AppForm.vue";
import AppComments from "./AppComments.vue";
import AppLoader from "./AppLoader.vue";
export default {
  data() {
    return {
      blocks: [],
      comments: [],
      loading: false,
    };
  },
  methods: {
    newBlock(block) {
      this.blocks.push(block);
    },
    async loadComments() {
      this.loading = true;
      const result = await fetch(
        "https://jsonplaceholder.typicode.com/comments?_limit=42"
      );
      this.comments = await result.json();
      this.loading = false;
    },
  },
  components: { AppResume, AppForm, AppComments, AppLoader },
};
</script>
