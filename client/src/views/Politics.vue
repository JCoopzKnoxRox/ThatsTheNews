<template lang="html">
  <div class="Politics">
    <h1>Political News</h1>
      <ol v-for="artic in articles" :key="artic.link">
      <h2><img :src= artic.image 
        width="800" 
        height="500"
      /></h2>
      <br> 
      <h2><a v-bind:href= artic.link>Link</a></h2>
      <br> <br> 
        <h2>
        {{ artic.title }} 
        </h2>
      <br>
      <div v-if="artic.text" >
        <h2><textarea rows ="10" cols = "200" v-model="artic.text" disabled=true dark=true></textarea> </h2>
      </div>
     
      <br> <br> <br>
      </ol>
      <p> You have reached the end of the news buffer, please check back another time to see more.</p>
  </div>
</template>


<script>
import PostsService from '@/services/PostsService'
export default {
    name: 'Politics',

    data() {
        return {
          articles: null
        }
    },
  mounted() {
    PostsService.get_articles("political")
      .then(response => {
        this.articles = response.data.slice(0,100)
      })
    }
  }


</script>


<style scoped lang="css">

h1 {
  text-align: center;
  color:rgb(230, 228, 228);
  background: linear-gradient(to right, #0400ff 0%, #fc0000 100%);
}
h2 {
  text-align: center;
}
ol {
  padding-left: 50px;
  padding-right: 50px;
  text-align:left;
  color:rgb(255, 253, 253);
  background-color: rgb(29, 29, 29);
  border: 2px solid black;
}
p {
  text-align: center;
  border: 15px solid black;
  color:rgb(230, 228, 228);
  background-color: rgb(29, 29, 29);
}
</style>