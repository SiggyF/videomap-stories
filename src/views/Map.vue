<template>
    <v-mapbox :access-token="accessToken" :map-style="mapStyle" ref="mapbox"></v-mapbox>
</template>
<script>
import Vue from 'vue'
import _ from 'lodash'
import Vue2MapboxGL from 'vue2mapbox-gl';

import stories from '@/assets/stories.json'


// You might want to import the relevant css, for example:
import 'mapbox-gl/dist/mapbox-gl.css'
// for the v-mapbox-geocoder
import '@mapbox/mapbox-gl-geocoder/dist/mapbox-gl-geocoder.css'
import mapboxgl  from 'mapbox-gl'

// Use the plugin
Vue.use(Vue2MapboxGL);

export default {
  data () {
    let story = _.find(stories, ['id', this.$route.params.id])
    console.log('story', story)
    let token = process.env.VUE_APP_MAPBOX_ACCESS_TOKEN
    return {
      accessToken: token,
      story: story,
      mapStyle: story.style,
      drawer: false,
      stories

    }
  },
  mounted () {
    // TODO: this should be in object
    this.map.on('load', () => {
      this.addControls()
      this.addLayers()
    })

  },
  computed: {
    map () {
      let map = this.$refs.mapbox.map
      return map
    }

  },
  methods: {
    addControls () {
      let map  = this.map
      map.addControl(new mapboxgl.NavigationControl())
      map.addControl(new mapboxgl.ScaleControl(), 'bottom-right')
    },
    addLayers () {
      // let a =  this.map.flyTo(
      //   this.story.location
      // )
      // console.log('a', a)

      this.map.flyTo(
        {
          speed: 0.5,
          ...this.story.location,
          pitch: 0
        }
      )
      this.story.layers.forEach(
        layer => {
          console.log('adding layer', layer)
          this.map.addLayer(layer)
          // assume source has same name as layer
          let source = this.map.getSource(layer.id)
          if (source.player) {
            // pass fps and timestep
            source.player.play(15, 0.1)
          }
        }
      )
    }
  }
}
</script>
<style>
  .mapboxgl-map {
  height: 100%;
  width: 100%;
}
</style>
