<template>
    <div class="personProfile">
        <h1>The G95-WebPage</h1>
    
      <div class="jobs" v-if="data && data.length" v-for="(person, index)  in data" v-bind:key='"person" + index' :person='person'>
      
          
            <div class="card-text">
              <h4>{{person.firstName}} {{person.lastName}}</h4>
              <img class="g95" height="350" width="350" v-bind:src="person.imgUrl">
            </div>
      
        
      </div>
    
  </div>
</template>

<script>
import axios from 'axios'
import BootstrapVue from 'bootstrap-vue'
export default {
    name: "Person",
    data(){
        return {
            data: [],
            apiURL: "https://g95-server.herokuapp.com/g95/"
        }
    },
    mounted () {
        axios.get(this.apiURL)
    .then(response => {
    //   console.log(response.data.data.person[0].firstName)
      this.data = response.data.data
    //   console.log(data.firstName[0])
    }) 
  }
    
}
</script>

<style>

</style>
