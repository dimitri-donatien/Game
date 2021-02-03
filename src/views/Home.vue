<template>
  <div class="home">

    <section v-if="errored">
      <p>Nous sommes désolés, nous ne sommes pas en mesure de récupérer ces informations pour le moment. Veuillez réessayer ultérieurement.</p>
    </section>

    <section class="container-card" v-else>

      <div v-if="loading">Chargement...</div>

      <div v-for="info in infos" :key="info.id">
        <MyCard :title="info.title" :thumbnail="info.thumbnail" :short_description="info.short_description" :genre="info.genre" :release_date="info.release_date" :game_url="info.game_url"></MyCard>
      </div>

    </section>

  </div>
</template>

<script>
// @ is an alias to /src
import { reactive, toRefs, onMounted } from 'vue'
import MyCard from '@/components/MyCard.vue'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    MyCard
  },
  setup () {
    const state = reactive({
        infos: null,
        loading: true,
        errored: false
    })

    const options = {
      method: 'GET',
      url: 'https://free-to-play-games-database.p.rapidapi.com/api/games',
      headers: {
        'x-rapidapi-key': 'c4fab265c2mshddc2bc7fbe6a360p14074djsn0b3ae8817dd9',
        'x-rapidapi-host': 'free-to-play-games-database.p.rapidapi.com'
      }
    }

    const getInfos = () => {
    axios
      .request(options)
      .then(response => {
        state.infos = response.data
        console.log(state.infos)
      })
      .catch(error => {
        console.log(error)
        state.errored = true
      })
      .finally(() => state.loading = false)
    }

    onMounted(getInfos)

    return {
      ...toRefs(state),
    }
  }
}
</script>

<style scoped>
  .container-card {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    align-items: center;
    gap: 1rem;
    padding: 1rem;
  }
</style>