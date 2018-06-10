<template>
  <div>
    <h1>Search here </h1>
    <div class="search">
      <input type="text" placeholder="Search here" v-model="item" @keyup="search">
      <select name="" v-model="searchType" @click="search" id="select" > 
        <option value="movie">Movies</option>
        <option value="series">TV Series</option>
      </select>
    </div>

    <div class="container">
      <div v-for="movie in info" :key="movie.imdbID" v-if="selectedType" class="single-template">
        <img :src="movie.Poster" alt="">
        <h1>{{movie.Title}}</h1>
        <p>{{movie.Year}}</p>
      </div>
    </div>


  </div>
</template>

<script>

export default {
  
  name: 'movie',

  data(){
    return{
      info:[],
      item:"",
      searchType:''
    }
  },

methods:{
  search() {
      this.axios
      .get('http://www.omdbapi.com/?s='+encodeURIComponent(this.item)+'&apikey=e8ed16e8' + '&type=' + this.searchType)
      .then(response =>(this.info = response.data.Search))
  },


},
computed:{
      selectedType(){
    if(this.searchType == ""){
      return this.movie.Type == this.searchType;
    } else{
      return true;
    }
  }
}




}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.search {

  input {
    border:0.5px solid rgba($color: #2c3e50, $alpha: 0.6);
    border-radius: 20px;
    padding:10px 100px 10px 10px;
    font-weight: bolder;
    outline: none;
  }
  #select{
    height:30px;
    border-radius: 40px;
    width:80px;
    border:0.5px solid rgba($color: #2c3e50, $alpha: 0.6);
  }

}

  .container {
    max-width: 800px;
    margin:0 auto;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    padding:40px 20px;

    .single-template {
      box-sizing: border-box;
      padding: 10px;
      display: flex;
      flex-direction: column;
      justify-content: flex-start;
      align-items: center;
      width:33%;

      img {
       height: auto;
       width: 100%;
       
      }
      h1 {
      font-size: 20px;
      margin:5;
      }
      p {
        margin:0;
      }
    }
  }

</style>
