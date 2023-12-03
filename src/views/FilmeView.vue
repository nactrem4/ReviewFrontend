<template>
  <h1>Filme</h1>
  <div class="container-fluid">
    <div class="row row-cols-1 row-cols-md-4 g-4">
      <div class="col" v-for="film in filme" :key="film.id">
        <div class="card h-100">
            <h5 class="card-title">{{ film.filmName }} {{ film.filmBeschreibung }}</h5>
            <p class="card-text">
              {{ film.filmName }} {{ film.filmBeschreibung }}.
            </p>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'FilmeView',
  data () {
    return {
      filme: []
    }
  },
  mounted () {
    const endpoint = ('http://localhost:8080/api/v1/films')
    const requestOptions = {
      method: 'GET',
      redirect: 'follow'
    }

    fetch(endpoint, requestOptions)
      .then(response => response.json())
      .then(result => result.forEach(filme => {
        this.filme.push(filme)
      }))
      .catch(error => console.log('error', error))
  }
}
</script>

<style scoped>

</style>
