<template>
  <h1>Comantários</h1>
  <hr />
  <div class="form-todo form-group">
    <p>
      <input
        type="text"
        placeholder="nome"
        name="author"
        class="form-control"
        v-model="name"
      />
    </p>
    <p>
      <textarea
        name="message"
        placeholder="Comentário"
        class="form-control"
        v-model="message"
      ></textarea>
    </p>
    <button type="submit" class="btn btn-primary" v-on:click="addComment">
      Comentar
    </button>
  </div>
</template>

<script>
export default {
  data: () => ({
    name: "",
    message: "",
  }),
  emits: ["add-comment"],
  methods: {
    addComment() {
      const { name, message } = this;
      if (message.trim()) {
        this.$emit("add-comment", { name, message });
        this.name = "";
        this.name = "";
      }
    },
  },
};
</script>