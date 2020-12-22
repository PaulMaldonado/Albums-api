<template>
  <div>
      <div class="container">
          <div class="row">
              <div class="col-md-5 col-sm-12 col-lg-5 col-xl-5 col-xxl-5 mx-auto">
                  <div class="card mt-4">
                      <div class="card-header">Crear nuevo album</div>
                      <div class="card-body">
                          <div class="form-group">
                              <input v-model="title" type="text" placeholder="Título" class="form-control">
                          </div>
                          <div class="form-group mt-4">
                              <input v-model="userId" type="number" placeholder="User id" class="form-control">
                          </div>

                          <div class="d-grid gap-2 mt-4">
                              <button class="btn btn-primary" @click.prevent="newAlbum">Guardar</button>
                          </div>
                      </div>
                  </div>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import router from '@/router'
import axios from 'axios'

export default {
    name: 'CreateAlbum',

    setup() {
        const title = ref('');
        const userId = ref('');
        const API_URL = 'https://jsonplaceholder.typicode.com/albums';

        function newAlbum() {
            axios.post(`${API_URL}`, {
                title: title.value,
                userId: userId.value
            })
            .then(() => {
                router.push('/')
            })
            .catch(error => {
                console.log(error)
            })
        }

        return {
            title,
            userId,
            newAlbum,
        }
    }
}
</script>

<style>

</style>