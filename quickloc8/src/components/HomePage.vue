<template>
  <div id="loading" ref="loading">
    <img alt="Oooops" src="../assets/quickloc8.svg" />
    <h3>Loading.....</h3>
  </div>
  <div id="mapping" ref="mapping"></div>
</template>

<script>
import { Loader } from '@googlemaps/js-api-loader';

export default {

  name: "HomePage",

  mounted() {




    /*Loader Disapper*/
    const load = this.$refs.loading;
    setTimeout(() => {
      load.style.display = "none";
      const loader = new Loader({
  apiKey: "AIzaSyDltxY3QD3xHuQYknWp0qOybaA4RVBH6Hk",

});
const mapOptions = {
  center: {
    lat: -33.8,
    lng: 18.8
  },
  zoom: 10,
  libraries:["places"]
};
loader.load().then((google) => {
    new google.maps.Map(this.$refs.mapping, mapOptions);
  })
  .catch(e => {
  console.log(e)
  });
    }, 3500);
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#mapping{
  position:absolute;
  top:100vh;
  left:0;
  height:100vh;
  width:100vw;
 
  
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
