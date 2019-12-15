<template>
  <div class="container">
    <form id="form" method="POST" @submit="validateForm">
      <label for="textInput">Text input Label</label>
      <input
        type="text"
        id="textInput"
        name="textInput"
        class="form-control"
        placeholder="Text input"
        v-bind:class="{'is-invalid': attemptSubmit && missingText}"
      >
      <p>
        <small class="helper" v-if="attemptSubmit && missingText">cannot be empty</small>
      </p>

      <label for="emailInput">Email Label</label>
      <input
        type="email"
        id="emailInput"
        name="emailInput"
        class="form-control"
        placeholder="Email input"
        v-bind:class="{'is-invalid': attemptSubmit && missingEmail}"
      >
      <p>
        <small class="helper" v-if="attemptSubmit && missingText">cannot be empty</small>
      </p>

      <div class="input-group mb-4">
        <input
          type="file"
          ref="file"
          name="fileInput"
          class="custom-file-input"
          id="fileInput"
          aria-describedby="fileInput"
        >
        <label class="custom-file-label" for="fileInput">File Label</label>
      </div>
      <input class="btn btn-info btn-block my-4" type="submit">
    </form>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      textInput: "",
      emailInput: "",
      attemptSubmit: false
    };
  },
  computed: {
    missingText() {
      return this.textInput === "";
    },
    missingEmail() {
      return this.emailInput === "";
    }
  },
  methods: {
    validateForm: function(event) {
      this.attemptSubmit = true;
      if (this.missingText || this.missingEmail) event.preventDefault();
      const file = this.$refs.file.files[0];

      if (!file) {
        event.preventDefault();
        alert("No file chosen");
        return;
      }

      if (file.size > 1024 * 1024) {
        event.preventDefault();
        alert("File too big (> 1MB)");
        return;
      }

      alert("File OK");
    }
  }
};
</script>

<style scoped>
.container {
  margin: 2em;
  height: 200vh;
}
</style>