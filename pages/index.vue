<template>
  <div style="padding:50px">
    <v-row justify="center" align="center">
      <v-col cols="12" sm="8" md="6">
        <div class="text-center">
          <v-img lazy-src="/storyblocks-logo.jpg" src="/storyblocks-logo.jpg"></v-img>
          <h2>Unofficial Downloader</h2>
        </div>
        <br>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-text-field
            v-model="url"
            label="Paste URL"
            outlined
            style="padding-right:20px; padding-left:20px"
      ></v-text-field>
      <div class="text-left">
        <v-btn
          x-large
          rounded
          color="yellow"
          style="padding-right:20px; padding-left:20px"
          @click.prevent='getDownloadLink'
        >
          Download Now
        </v-btn>
      </div>
    </v-row>
    <br>
    <v-row v-if="loading" justify="center">
      <v-img
        src="/Loading.gif"
        max-width="200"
      >
      </v-img>
    </v-row>
    <div v-if="showDownloadLink">
      <h3 class="text-center">Download Now</h3>
      <br>
      <p class="text-center">{{resp.title}}</p>
      <br><br>
      <v-row justify="center">
        <v-img 
          :lazy-src="resp.thumbnail"
          :src="resp.thumbnail"
          max-width="360"
        >
        </v-img>
      </v-row>
      <br><br>
      <v-row justify="center">
        <v-btn
          large
          rounded
          color="primary"
          style="padding-right:20px; padding-left:20px"
          @click.prevent='toDownloadLink(resp.result)'
        >
          Download Now
        </v-btn>
      </v-row>
    </div>
  </div>
</template>

<script>
// import Logo from '~/components/Logo.vue'
// import VuetifyLogo from '~/components/VuetifyLogo.vue'
import axios from 'axios'

export default {
  data () {
    return {
      url: "",
      downloadLink: "",
      showDownloadLink: false,
      loading: false,
      resp: {} 
    }
  },
  head() {
      return {
        title: "Storyblocks Unofficial Downloader",
      }
  },
  methods: {
    getDownloadLink() {
      if(this.url == "") {
        alert("Invalid Link")
      }
      else {
        this.loading = true
        this.showDownloadLink = false
        axios.post('https://angry-ritchie-79cd58.netlify.app/.netlify/functions/api/generate', {url: this.url})
        .then((response) => {
          this.resp = response.data
          this.showDownloadLink = true
          this.loading = false
        })
        .catch((error) => {
          console.log(error)
          alert("Invalid Link")
        })
      }
    },
    toDownloadLink(url) {
      window.open(url)
    }
  }
}
</script>
