<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
      <router-link class="navbar-brand" to="/"><img src="../assets/logo-dark.png" alt="logo" width="250" height="100"></router-link>
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
        <ul class="navbar-nav ml-auto">
          <li class="nav-item">
            <button type="button" class="btn btn-success my-2 btn-block">
              <router-link class="nav-link active" aria-current="page" to="/login">Login</router-link>
            </button>
          </li>
            <li class="nav-item">
            <button type="button" class="btn btn-success my-2 btn-block">
              <router-link class="nav-link active" aria-current="page" to="/register">S'inscrire</router-link>
            </button>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
