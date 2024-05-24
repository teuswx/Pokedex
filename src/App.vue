<script setup>
</script>

<template>
  <!--Navbar-->
  <nav class="navbar navbar-expand-lg navbar-dark bg-warning">
    <div class="container-fluid">
      <router-link class="navbar-brand" to="/">
        <img src="./assets/icon.png" alt="Logo" width="30" height="24" class="d-inline-block align-text-top">
        PokeVite
      </router-link>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
        aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <router-link class="nav-link" aria-current="page" to="/">Home</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/about">About</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>

  <!-- CONTENT -->
  <div class="main">
    <router-view></router-view>
  </div>

  <footer class="bg-warning text-light">
    <div>Design in {{ new Date().getFullYear() }}</div>
  </footer>
</template>

<style>
body{
  height: 100vh;
  background: rgb(247,255,187);
background: linear-gradient(0deg, rgba(247,255,187,1) 0%, rgba(245,254,102,1) 100%);
}
footer {  
  position: fixed;
  bottom: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 56px;
}
</style>
