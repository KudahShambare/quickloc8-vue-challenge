<template>
  <div id="loading" ref="loading">
    <img alt="Oooops" src="../assets/quickloc8.svg" />
    <h3>Loading.....</h3>
  </div>
  <div id="msg-link" ref="msglink">
    <router-link to="/messages">
      <button>View Messages</button>
    </router-link>
  </div>
  <div id="mapping" ref="mapping"></div>
</template>

<script>
import { Loader } from "@googlemaps/js-api-loader";

export default {
  name: "HomePage",

  mounted() {
    /*Loader Disapper*/
    const load = this.$refs.loading;
    const mapping = this.$refs.mapping;
    const msgLink = this.$refs.msglink;

    setTimeout(() => {
      load.style.display = "none";
      mapping.style.visibility = "visible";
      msgLink.style.display = "block";
    }, 3500);
    const loader = new Loader({
      apiKey: "AIzaSyDltxY3QD3xHuQYknWp0qOybaA4RVBH6Hk",
    });
    const mapOptions = {
      center: {
        lat: -33.8,
        lng: 18.8,
      },
      zoom: 10,
      libraries: ["places"],
    };
    loader
      .load()
      .then((google) => {
        new google.maps.Map(mapping, mapOptions);
      })
      .catch((e) => {
        console.log(e);
      });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#loading {
  text-align: center;
}
#msg-link {
  visibility: "hidden";

  display: none;
  top: 0;
  left: 0;
  width: 100vw;
}
#mapping {
  visibility: hidden;
  position: absolute;
  top: 15vh;
  left: 0;
  height: 100vh;
  width: 100vw;
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
