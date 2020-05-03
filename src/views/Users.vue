<template>
  <div>
    <div v-if="!list.length" class="alert alert-warning">
      Нет пользователей
    </div>
    <user-list v-else :list="list" @click="removeFromList"></user-list>

    <button type="button" class="btn btn-success" @click="loadData">
      Загрузить данные
    </button>
  </div>
</template>

<script>
import UserList from '@/components/UserList.vue';
import axios from 'axios';

export default {
  name: 'UserListPage',
  components: {
    UserList,
  },
  data: () => ({
    list: [],
  }),
  methods: {
    loadData() {
      axios.get('http://localhost:3004/users').then(response => {
        this.list = response.data;
      });
    },
    removeFromList(id) {
      this.list = this.list.filter(item => item.id !== id);
    },
  },
};
</script>

<style></style>
