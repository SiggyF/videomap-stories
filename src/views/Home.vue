<template>
<div>
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
          class="ma-3 pa-2"
          outlined
          tile

          >
          <v-img
            class="white--text align-end"
            :src="story.image"
            height="200px"
            width="400px"
            >
            <v-card-title v-text="story.title">
            </v-card-title>
          </v-img>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn icon :to="'/stories/' + story.id">
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
      stories
    }
  }

}
</script>
