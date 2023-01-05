<template>
  <div>
    <div>
      <input type="text" v-model="zip">
      <button @click="search()">search</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "TableContainer",
  data: function () {
    return {
      zip: "",
      long: "",
      lat: ""
    }
  },
  methods: {
    search(){
      const requestUrl = "https://maps.googleapis.com/maps/api/geocode/json?address=" + this.zip + "&key=AIzaSyDKEmPCn83JvdWJAKo4SeTZrcF7YzU6QeQ";
      axios.get(requestUrl)
      .then(res => {
        console.log(res.data)
        this.long = res.data.results[0].geometry.location.lng;
        this.lat = res.data.results[0].geometry.location.lat;
      })
      .catch(err => {
        console.log(err);
      })
      .then( res => {
              console.log(this.long);
      console.log(this.lat);
      })
    }
  }
}
</script>

<style>

</style>