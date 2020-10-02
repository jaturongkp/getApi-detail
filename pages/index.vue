<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand href="#">
        Anime
      </b-navbar-brand>

      <b-navbar-toggle target="nav-collapse" />

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item href="#">
            Link
          </b-nav-item>
          <b-nav-item href="#" disabled>
            Disabled
          </b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <div class="container">
      <b-input-group class="mt-5">
        <b-form-input v-model="keyword" type="text" />
        <b-input-group-append>
          <b-button variant="outline-primary" @click="searchData()">
            Search Anime
          </b-button>
        </b-input-group-append>
      </b-input-group>
      <div>
        <b-card-group columns>
          <b-card
            v-for="data in resultData"
            :key="data.mal_id"
            :title="data.title"
            :img-src="data.image_url"
            img-alt="Image"
            img-top
            img-width="500px"
            tag="article"
            style="max-width: 20rem;"
            class=" mt-3 mb-2"
          >
            <b-button class="mr-2" :href="data.url" variant="primary">
              Link
            </b-button>
            <nuxt-link :to="{ name: 'product-id', params: { id: data } }">
              <b-button variant="danger">
                Detail
              </b-button>
            </nuxt-link>
          </b-card>
        </b-card-group>
      </div>
    </div>
  </div>
</template>

<script>
import Axios from 'axios'
export default {
  data () {
    return {
      resultData: null,
      keyword: ''
    }
  },

  methods: {
    searchData () {
      console.log('searchData')
      Axios.get(
        'https://api.jikan.moe/v3/search/anime?q=' + this.keyword + '&page=1'
      )
        .then((response) => {
          this.resultData = response.data.results
        })
        .catch((err) => {
          console.log(err)
        })
    }
  }
}
</script>

<style></style>
