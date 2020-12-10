<template>
  <form>
    <label for="input-author">Autor</label>
    <input
      type="text"
      name="author"
      id="input-author"
      placeholder="Autor"
      v-model="author"
    />
    <label for="area-comment">Comentário</label>
    <textarea
      name="description"
      id="area-comment"
      rows="4"
      cols="10"
      placeholder="Adicione um comentário"
      v-model="description"
    />
    <button v-on:click.prevent="addComment" type="submit">
      Novo comentário
    </button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      author: "",
      description: "",
    };
  },
  methods: {
    addComment() {

      if(!this.description.trim()){
        return;
      }
      
      this.$emit("add-to-comments", {
        author: this.author,
        description: this.description,
      });
      this.author = "";
      this.description = "";
    },
  }
};
</script>

<style scoped>
form {
  height: 40vh;
  display: flex;
  flex-direction: column;
}

input[type="text"],
label,
textarea {
  width: 50vw;
  margin: 5px auto;
}

button[type="submit"] {
  background-color: #4caf50;
  color: white;
  font-size: 0.8em;
  padding: 15px 32px;
  border: 0;
  font-weight: 700;
  margin: 5px auto;
}
</style>