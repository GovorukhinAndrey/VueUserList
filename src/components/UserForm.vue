<template>
  <div>
    <div class="form-group">
      <label>Имя</label>
      <input type="text" class="form-control" v-model="localUser.firstName" />
    </div>

    <div class="form-group">
      <label>Фамилия</label>
      <input type="text" class="form-control" v-model="localUser.lastName" />
    </div>

    <div class="form-group">
      <label>Email</label>
      <input type="text" class="form-control" v-model="localUser.email" />
    </div>

    <div class="form-group">
      <label>URL картинки</label>
      <input type="text" class="form-control" v-model="localUser.picture" />
    </div>

    <div class="form-group">
      <label>Возраст</label>
      <input type="text" class="form-control" v-model="localUser.age" />
    </div>

    <div class="form-group">
      <label>Активен</label>
      <div class="custom-control custom-checkbox">
        <input
          type="checkbox"
          class="custom-control-input"
          id="same-address"
          v-model="localUser.isActive"
        />
        <label v-if="localUser.isActive" class="custom-control-label" for="same-address">да</label>
        <label v-else class="custom-control-label" for="same-address">нет</label>
      </div>
    </div>

    <div class="form-group">
      <label>Email</label>
      <input type="text" class="form-control" v-model="localUser.email" />
    </div>

    <div class="form-group">
      <label>Уровень доступа</label>
      <select class="custom-select d-block w-100" v-model="localUser.accessLevel">
        <option>admin</option>
        <option>user</option>
        <option>guest</option>
      </select>
    </div>

    <div class="form-group">
      <label>Баланс</label>
      <input type="text" class="form-control" v-model="localUser.balance" />
    </div>

    <div class="form-group">
      <label>Телефон</label>
      <input type="text" class="form-control" v-model="localUser.phone" />
    </div>

    <div class="form-group">
      <label>Адрес</label>
      <input type="text" class="form-control" v-model="localUser.address" />
    </div>

    <div class="form-group">
      <label>Компания</label>
      <input type="text" class="form-control" v-model="localUser.company" />
    </div>

    <div class="form-group">
      <label>Биография</label>
      <input type="text" class="form-control" v-model="localUser.about" />
    </div>

    <div class="form-group">
      <label>Дата регистрации</label>
      <input type="text" class="form-control" v-model="localUser.registered" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'UserForm',
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
  data: () => ({
    localUser: null,
  }),
  created() {
    this.updateUser();
  },
  watch: {
    // При изменении локального состояния
    // отправляем объект наверх
    localUser: {
      deep: true,
      handler() {
        this.$emit('input', this.localUser);
      },
    },
  },
  methods: {
    updateUser() {
      this.localUser = Object.assign({}, this.user);
    },
  },
};
</script>

<style></style>
