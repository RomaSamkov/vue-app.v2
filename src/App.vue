<template>
  <div class="form-container">
    <h2>{{ message }}</h2>
    <form @submit.prevent="submitForm">
      <label for="name">Name:</label>
      <input type="text" id="name" v-model="name" />
      <label for="email">Email:</label>
      <input type="email" id="email" v-model="email" />
      <button type="submit">Submit</button>
    </form>
    <ul v-if="submissions.length > 0">
      <li v-for="(submission, index) in submissions" :key="index">
        <p>Name:{{ submission.name }}</p>
        <p>Email:{{ submission.email }}</p>
        <button @click="deleteSubmission(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      name: "",
      email: "",
      submissions: [],
    };
  },
  methods: {
    submitForm() {
      const newSubmissions = {
        name: this.name,
        email: this.email,
      };
      this.submissions.push(newSubmissions);
      this.name = "";
      this.email = "";
    },
    deleteSubmission(index) {
      this.submissions.splice(index, 1);
    },
    showMessage() {
      alert("Hello World");
    },
  },
  computed: {
    message() {
      const count = this.submissions.length;
      if (count === 0) {
        return "0 submissions";
      } else {
        return `${count} submissions`;
      }
    },
  },
};
</script>

<style>
.price-block {
  text-align: center;
}
</style>
