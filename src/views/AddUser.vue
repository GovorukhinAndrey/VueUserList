<template>
  <div>
    <h2>Добавление пользователя</h2>

    <div v-if="!user" class="alert alert-warning">
      ...Загрузка данных
    </div>
    <user-form v-else :user="user" @input="value => (user = value)"></user-form>

    <button type="button" class="btn btn-success btn-block" @click="saveChanges">
      Добавить пользователя
    </button>
  </div>
</template>

<script>
import UserForm from '@/components/UserForm.vue';
import axios from 'axios';

const emptyObj = {
  id: null,
  isActive: false,
  balance: '',
  picture: '',
  age: 0,
  accessLevel: '',
  firstName: '',
  lastName: '',
  company: '',
  email: '',
  phone: '',
  address: '',
  about: '',
  registered: '',
};

export default {
  name: 'AddUserPage',
  components: {
    UserForm,
  },
  data: () => ({
    user: emptyObj,
    url: 'http://localhost:3004/users/',
  }),
  methods: {
    saveChanges() {
      axios.post(this.url, this.user).then(() => {
        this.$route.push({ path: '/users' });
      });
    },
  },
};
</script>

<style></style>
