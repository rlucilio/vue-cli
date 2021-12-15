<template>
  <div class="container">
    <form-comment @add-comment="addComment"></form-comment>
    <div class="list-group">
      <div>
        <p v-if="comments.length < 1">Sem comentários</p>
        <div
          v-else
          class="list-group-item"
          v-for="(comment, index) in allComments"
          :key="index"
        >
          <span class="comment__author"
            >Autor: <strong>{{ comment.name }}</strong></span
          >
          <p>{{ comment.message }}</p>
          <div>
            <a
              href="#"
              title="Excluir"
              v-on:click.prevent="removeComment(index)"
              >Excluir</a
            >
          </div>
        </div>
      </div>
    </div>
    <hr />
  </div>
</template>

<script>
import FormComment from "./FormComment.vue";
export default {
  components: {
    FormComment,
  },
  data: () => ({
    comments: [],
    name: "",
    message: "",
  }),
  methods: {
    addComment(event) {
      console.log(event);
      this.comments.push({
        name: event.name.trim(),
        message: event.message.trim(),
      });
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    },
  },
  computed: {
    allComments() {
      return this.comments.map((comment) => ({
        ...comment,
        name: comment.name.trim() ? comment.name.trim() : "Anonimo",
      }));
    },
  },
  watch: {
    comments: {
      handler(val) {
        console.log(val);
      },
      deep: true,
    },
  },
};
</script>