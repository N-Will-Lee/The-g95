<template>
    <div class="personProfile">
        <h1>The G95-WebPage</h1>
    <b-container class="jobContainer">
      <div class="jobs" v-if="data && data.length" v-for="(data, index)  in data" v-bind:key='"data" + index' :data='data'>
        <b-row class="text-center">
          <b-card bg-variant="info" text-variant="white" class="text-center">
            <b-col class="card-text">
              <h4>{{firstName}} {{lastName}}</h4>
            </b-col>
           
            <div class="buttons">
              <b-button class="requesttheJob">Request Job</b-button>
            </div>
          </b-card>
        </b-row>
      </div>
    </b-container>
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
      console.log(response.data.data)
      this.data = response.data
    }) 
  }
    
}
</script>

<style>

</style>
