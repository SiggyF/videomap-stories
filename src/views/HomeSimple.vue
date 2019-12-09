<template>
<div>
  <router-link :to="'/stories/' + story.id" v-for="story in stories" :key="story.id">{{ story.title }}</router-link>
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
