<template>
  <nav class="navbar navbar-expand-lg bg-dark" data-bs-theme="dark">
    <div class="container">
      <a class="px-2" href="#">
        <img src="/img/logo.png" alt="Bootstrap" width="30" height="24" />
      </a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link to="/">
              <a class="nav-link active" aria-current="page"> Home </a>
            </router-link>
          </li>
          <li class="nav-item">
            <router-link to="/pedidos">
              <a class="nav-link text-decoration" aria-current="page"> Pedidos </a>
            </router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "navbar",
};
</script>

<style scoped>
a{
  text-decoration: none;
}
</style>
