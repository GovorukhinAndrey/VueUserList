<template>
  <div>
    <h2>Edit Page.</h2>
    <h3>Пользователь с id: {{ id }}</h3>
    <pre>{{ user }}</pre>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'EditUserPage',
  computed: {
    id() {
      return this.$route.params.id;
    },
  },
  data: () => ({
    user: null,
  }),
  mounted() {
    this.getUser();
  },
  methods: {
    getUser() {
      axios
        .get(`http://localhost:3004/users/${this.id}`)
        .then(response => (this.user = response.data));
    },
  },
};
</script>

<style></style>
