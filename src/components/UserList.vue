<template>
  <table class="table table-hover">
    <thead>
      <tr>
        <th>
          id
        </th>
        <th>
          firstName
        </th>
        <th>
          lastName
        </th>
        <th>
          Удалить
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in list" :key="item.id">
        <td>
          <router-link :to="`/users/${item.id}`"> #{{ item.id }} </router-link>
        </td>
        <td>
          {{ item.firstName }}
        </td>
        <td>
          {{ item.lastName }}
        </td>
        <td>
          <button type="button" @click="removeUser(item.id)">
            x
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'UserList',
  props: {
    list: {
      type: Array,
      required: true,
    },
    title: {
      type: String,
      default: 'Заголовок',
    },
  },
  methods: {
    removeUser(id) {
      this.$emit('click', id);
    },
  },
};
</script>

<style></style>
