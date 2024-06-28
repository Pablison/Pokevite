<script setup>
import { ref } from 'vue';
let num = ref(0)

</script>

<template>
  <nav class="navbar navbar-expand-lg navbar-dark">
    <div class="container-fluid">
      <router-link class="navbar-brand" to="/">
        <img src="https://cdn-icons-png.flaticon.com/512/188/188987.png" alt="Logo" width="30" height="24"
          class="d-inline-block align-text-top">
        Pokevite
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
  <footer class="text-light">
    <div>
      Design in {{ new Date().getFullYear() }}
    </div>
  </footer>
</template>

<style>
body{
  height: 100vh;
  background-image: linear-gradient(to top, #d5d4d0 0%, #d5d4d0 1%, #eeeeec 31%, #efeeec 75%, #e9e9e7 100%);
}
footer {
  position: fixed;
  bottom: 0;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 30px;
  background-color: #72A0C1;
}
nav{
  background-color: #72A0C1;
}
.navbar{
  height: 45px;
  font-weight: bold;
}
</style>
