<template>
<v-app>
  <v-content>
    <v-navigation-drawer
      v-model="drawer"
      app
      >
      <v-list dense>
        <v-list-item link :to="{name: 'home'}">
          <v-list-item-action >
            <v-icon>mdi-home</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Home</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <template v-for="item in stories" >
          <v-list-item link :to="{name: 'map', params: {id: item.id}}" :key="item.id" >
            <v-list-item-action>
              <v-icon>mdi-map</v-icon>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      app
      >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>Video Maps</v-toolbar-title>
    </v-app-bar>

    <v-container fluid class="fill-height">
      <router-view :key="$route.fullPath"></router-view>
    </v-container>

  </v-content>
</v-app>
</template>

<script>
import stories from '@/assets/stories.json'
export default {
  name: 'App',

  components: {
  },
  data () {
    return {
      drawer: false,
      stories
    }
    //
  }
};
</script>
<style>
</style>
