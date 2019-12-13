<template>
<div class="fill-height">
  <v-container
    class="fill-height"
    fluid
    >
    <v-col
      cols="12">
      <v-row
        align="center"
        justify="center"
        >
        <v-card

          v-for="(story, index) in stories"
          :key="index"
          class="ma-3 story"
          :to="{name: 'map', params: {id: story.id}}"
          outlined
          tile

          >
          <v-img
            class="white--text align-end"
            :src="story.image"
            height="200px"
            width="400px"
            >
          </v-img>

          <v-card-title v-text="story.title">
          </v-card-title>
          <v-card-subtitle>
            {{ story.subtitle }}
          </v-card-subtitle>
          <v-card-text>

          </v-card-text>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn icon>
              <v-icon>mdi-heart</v-icon>
            </v-btn>

            <v-btn icon>
              <v-icon>mdi-share-variant</v-icon>
            </v-btn>
            <v-btn icon :to="{name: 'map', params: {id: story.id}}">
              <v-icon>mdi-presentation-play</v-icon>
            </v-btn>

          </v-card-actions>
        </v-card>


      </v-row>
    </v-col>
  </v-container>
</div>
</template>
<script>
import stories from '@/assets/stories.json'
export default {
  data () {
    return  {
      drawer: false,
      stories
    }
  }

}
</script>
<style>
.v-card.story {
  max-width: 400px;
}
.v-card.story .v-image  {
  max-height: 200px;
  height:  200px;
}
</style>
