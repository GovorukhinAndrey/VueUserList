<template>
  <div id="app">
    <nav class="navbar navbar-expand-md navbar-dark fixed-top bg-dark">
      <router-link to="/" class="navbar-brand"> Vue SPA </router-link>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarCollapse"
        aria-controls="navbarCollapse"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarCollapse">
        <ul class="navbar-nav mr-auto">
          <router-link tag="li" class="nav-item active" to="/" exact>
            <a class="nav-link" href="#">Home</a>
          </router-link>
          <router-link tag="li" class="nav-item" to="/users" exact>
            <a class="nav-link" href="#">Список пользователей</a>
          </router-link>
        </ul>
        <form class="form-inline mt-2 mt-md-0">
          <input
            class="form-control mr-sm-2"
            type="text"
            placeholder="Search"
            aria-label="Search"
          />
          <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
        </form>
      </div>
    </nav>

    <main role="main" class="container">
      <router-view> </router-view>
    </main>
  </div>
</template>

<style lang="scss">
#app {
  margin-top: 80px;
}
</style>
