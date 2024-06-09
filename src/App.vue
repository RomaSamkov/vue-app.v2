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
};
</script>

<style>
.price-block {
  text-align: center;
}
</style>
