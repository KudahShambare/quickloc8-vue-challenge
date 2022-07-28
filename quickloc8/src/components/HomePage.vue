

<template>
 <div id="loading" ref="loading"> 
 <img alt="Oooops" src="../assets/quickloc8.svg"/>
 <h3> Loading.....</h3>
 <vue-loaders-ball-beat/>
 </div>
</template>

<script>
//import loaders from npm



export default {
  name: 'HomePage',
 

  mounted(){
  const load = this.$refs.loading;
  console.log(load);
  setTimeout(()=>{
    load.style.display="none";
  },3500)
  }


}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
