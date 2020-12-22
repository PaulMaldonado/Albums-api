<template>
  <div>
      <nav class="navbar navbar-expand-lg navbar-dark bg-dark p-4">
          <router-link to="/" class="navbar-brand">Albums</router-link>
          <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>

          <div class="collapse navbar-collapse justify-content-end" id="navbarSupportedContent">
              <ul class="navbar-nav">
                  <li class="nav-item">
                      <router-link to="/create" class="nav-link active">Crear album</router-link>
                  </li>
              </ul>
          </div>
      </nav>
  </div>
</template>

<script>
export default {
    name: 'Navbar'
}
</script>

<style scoped>
    .navbar-brand {
        margin-left: 20px;
    }
</style>