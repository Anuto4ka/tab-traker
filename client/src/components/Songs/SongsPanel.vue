<template>
  <panel title="Songs">
    <v-btn
      :to="{
        name: 'songs-create'
      }"
      slot="action"
      class="cyan"
      fab
      absolute
      right
      middle
      >
      <v-icon>add</v-icon>
    </v-btn>
    <div
      class="song"
      v-for="song in songs"
      :key="song.id">

      <v-layout>
        <v-flex xs6>
          <div class="song-title">
            {{song.title}}
          </div>
          <div class="song-artist">
            {{song.artist}}
          </div>
          <div class="song-genre">
            {{song.album}}
          </div>

          <v-btn
            dark
            class="cyan"
            :to="{
              name: 'song',
              params: {
                songId: song.id
              }
            }">
            View
          </v-btn>
        </v-flex>

        <v-flex xs6>
          <img class="album-image" :src="song.albumImage" alt="">
        </v-flex>
      </v-layout>
    </div>
  </panel>
</template>

<script>
import SongsService from '@/services/SongsService'
export default {
  data () {
    return {
      songs: null
    }
  },
  watch: {
    '$route.query.search': {
      immediate: true,
      async handler (value) {
        this.songs = (await SongsService.index(value)).data
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .song{
    padding:20px;
  }
  .song-title{
    font-size:30px;
  }
  .song-artist{
    font-size:24px;
  }
  .song-genre{
    font-size:18px;
  }
</style>
