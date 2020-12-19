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
            v-model="title"
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
        >
          Download Now
        </v-btn>
      </div>
      </v-row>
  </div>
</template>

<script>
// import Logo from '~/components/Logo.vue'
// import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  components: {
    
  }
}
</script>
