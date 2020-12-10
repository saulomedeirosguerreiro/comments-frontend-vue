<template>
  <div id="comments">
    <h1>Comentários</h1>
    <CommentForm v-on:add-to-comments="addToComments" />
    <div class="comment-list">
      <div
        class="comment-item"
        v-for="(comment, index) in comments"
        v-bind:key="index"
      >
        <span><strong>Autor:</strong> {{ comment.author }}</span>
        <p><strong>Descrição: </strong>{{ comment.description }}</p>
        <button v-on:click="removeComment(index)" type="button">Remover</button>
      </div>
    </div>
  </div>
</template>

<script>
import CommentForm from "./CommentForm";
export default {
  components: {
    CommentForm,
  },
  data() {
    return {
      comments: [],
    };
  },
  mounted() {
    const commentListStorage = localStorage.getItem("comments");
    if (commentListStorage) {
      this.comments = JSON.parse(commentListStorage);
    }
  },
  methods: {
    addToComments(comment) {
      this.comments.push(comment);
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    },
  },
  computed: {
    allComments() {
      return this.comments.map((comment) => ({
        ...comment,
        name: comment.name.trim() === "" ? "Anônimo" : comment.name,
      }));
    },
  },
  watch: {
    comments() {
      localStorage.setItem("comments", JSON.stringify(this.comments));
    },
  },
};
</script>

<style scoped>
h1 {
  width: 50vw;
  margin: 5px auto;
}

.comment-list {
  height: 60vh;
  display: flex;
  flex-direction: column;
  overflow: auto;
}

.comment-item {
  width: 50vw;
  margin: 5px auto;
  background-color: #d3d3d3;
  border-radius: 0.375rem;
  padding: 10px 15px;
}
</style>