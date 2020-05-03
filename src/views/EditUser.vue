<template>
  <div>
    <h2>Редактирование пользователя</h2>
    <h3>{{ title }}</h3>

    <div v-if="!user" class="alert alert-warning">
      ...Загрузка данных
    </div>
    <user-form v-else :user="user" @input="value => (user = value)"></user-form>
    <!-- <user-form v-else :user="user"></user-form> -->

    <button type="button" class="btn btn-success btn-block" @click="saveChanges">
      Сохранить изменения
    </button>
    <button type="button" class="btn btn-danger btn-block" @click="removeUser">
      Удлить пользователя
    </button>
  </div>
</template>

<script>
import axios from 'axios';
import UserForm from '@/components/UserForm.vue';

export default {
  name: 'EditUserPage',
  components: {
    UserForm,
  },
  data: () => ({
    user: {
      firstName: '',
      lastName: '',
      phone: '',
    },
    restUrl: 'http://localhost:3004/users/',
  }),
  computed: {
    id() {
      return this.$route.params.id;
    },

    url() {
      return `${this.restUrl}${this.id}`;
    },

    title() {
      return !this.user.firstName || !this.user.LastName
        ? 'Пользователь'
        : [this.user.firstName, this.user.LastName, this.user.phone].join(' ');
    },
  },
  watch: {
    $route: 'loadData',
  },
  mounted() {
    this.loadData();
  },
  methods: {
    loadData() {
      axios.get(this.url).then(response => (this.user = response.data));
    },
    removeUser() {
      axios.delete(this.url).then(() => {
        this.$route.push({ path: '/users' });
      });
    },
    saveChanges() {
      axios.post(this.url, this.user).then(() => {
        this.$route.push({ path: '/users' });
      });
    },
  },
};
</script>

<style></style>
