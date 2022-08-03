<template>
  <div id="loading" ref="loading">
    <img alt="Oooops" src="../assets/quickloc8.svg" />
    <h3>Loading.....</h3>
  </div>
  <div id="msg-link" ref="msglink">
    <router-link to="/messages">
      <button > View Messages</button>
    </router-link>
  </div>
  <div id="mapping" ref="mapping"></div>
</template>

<script>

import { Loader } from "@googlemaps/js-api-loader";
import taxi from "../assets/taxi.png";
import vehicleLocations from "../vehicleCoordinates.json";

const towers=[
  {
    lat:'-25.757999',
    lng:'28.201021',
    range:'1000'
    },
     {
    lat:'28.201217651367',
    lng:'-25.75813293457',
    range:'1000'
    },
     {
    lat:'-25.757912',
    lng:'28.201139',
    range:'5607'
    },
]
console.log(towers)
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
      msgLink.style.height = "15vh";
            msgLink.style.position = "absolute";
      msgLink.style.textAlign = "center";
      msgLink.style.paddingTop="8vh"

            msgLink.style.left = "0";


    }, 3500);
    const loader = new Loader({
      apiKey: "AIzaSyDltxY3QD3xHuQYknWp0qOybaA4RVBH6Hk",
    });
    const mapOptions = {
      center: {
        lat: -33.8,
        lng: 18.8,
      },
      zoom: 5,
      libraries: ["places"],
    };

    loader
      .load()
      .then((google) => {
        const map = new google.maps.Map(mapping, mapOptions);
        vehicleLocations.forEach((vloc) => {
          new google.maps.Marker({
            position: {
              lat: parseFloat(vloc.latitude),
              lng: parseFloat(vloc.longitude),
            },
            map,
            icon: {
              url: taxi,
              scaledSize: new google.maps.Size(25, 25),
              rotation: parseFloat(vloc.heading),
            },
            title:"Taxi"
          });
        });
        towers.forEach((tower)=>{
          new google.maps.Marker({
            position:{
              lat:parseFloat(tower.lat),
              lng:parseFloat(tower.lng)
            },
            title:"Cellphone Tower",
            map
          })
          new google.maps.Circle({
            center:{
              lat:parseFloat(tower.lat),
              lng:parseFloat(tower.lng)
            },
            radius:parseFloat(tower.range)
            ,
            map
          })
        })
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
  padding-top:20vh;
}
button{
background-color:black;
color:white;
}
#msg-link {
  
background-color:skyblue;
visibility: "hidden";
text-align:"center";
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
