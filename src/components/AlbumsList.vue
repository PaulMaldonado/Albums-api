<template>
  <div> 
     <div class="container">
         <div class="row">
             <div class="col-md-4 col-sm-12 col-lg-4 col-xl-4 col-xxl-4" 
             v-for="album in albums" 
             :key="album.id"
             >

                 <div class="card mt-4">
                     <div class="card-body">
                         <h5 class="card-title">{{ album.title }}</h5>
                         <p class="card-text">{{ album.userId }}</p>

                         <button class="btn btn-danger" @click="deleteAlbum(album.id)">
                             Eliminar
                         </button>
                     </div>
                 </div>
             </div>
         </div>
     </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'
import axios from 'axios'

export default {
    name: 'AlbumsList',

    setup() {
        const API_URL = 'https://jsonplaceholder.typicode.com/albums';
        const albums = ref([]);

        function getAlbums() {
            axios.get(`${API_URL}`)
            .then(response => {
                albums.value = response.data;

                console.log(albums)
            })
        }

        function deleteAlbum(id) {
            axios.delete(`${API_URL}/${id}`)
                .then(() => {
                    albums.value.splice(id, 1)

                    getAlbums()
                })
                .catch(error => {
                    console.log(error)
                })
        }

        onMounted(() => {
               getAlbums()
        })

        return {
            albums,
            getAlbums,
            deleteAlbum
        }
    }
}
</script>

<style>

</style>