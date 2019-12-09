<template>
<div>
  <v-app>
    <v-content>
      <v-navigation-drawer
        v-model="drawer"
        app
        clipped
        >
        <v-list dense>
          <v-list-item link>
            <v-list-item-action>
              <v-icon>mdi-view-dashboard</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>Dashboard</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-list-item link>
            <v-list-item-action>
              <v-icon>mdi-settings</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>Settings</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>
      <v-app-bar
        app
        clipped-left
        >
        <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
        <v-toolbar-title>Video stories</v-toolbar-title>
      </v-app-bar>
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
                <v-btn icon :to="'/stories/' + story.id">
                  <v-icon>mdi-presentation-play</v-icon>
                </v-btn>

              </v-card-actions>
            </v-card>


          </v-row>
        </v-col>
      </v-container>
    </v-content>
  </v-app>
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
