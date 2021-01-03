<template>
  <div>
     <h1>Détails du restaurant qui a pour id : {{id}}</h1>
     <p>Nom : {{restaurant.name}}</p>
     <p>Cuisine : {{restaurant.cuisine}}</p>
     <p>Quartier : {{restaurant.borough}}</p>
     <p>Rue : {{restaurant.address.street}}</p>

    <h2>Voici où se trouve le restaurant sur la carte : </h2>
     <div class="mapRestau">
     <iframe
            class="styleMap"
            frameborder="0"
            style="border: 0"
            :src="recuperationCoordonnees()"
            allowfullscreen
          >
          </iframe>
      </div>

      <h2>Voici une image streetview avec les coordonnées du restaurant : </h2>
      <img :src="recuCoordImage()" alt="image du restaurant via streetview">

  </div>
</template>

<script>
export default {
  name: 'Restaurant',
  props: {
  },
  computed: {
      id(){
          console.log("caca = " + this.$route.params.id)
          return this.$route.params.id
          
      }
  },
  data: function() {
      return {
        //sourceIMG:"https://maps.googleapis.com/maps/api/streetview?&key=AIzaSyDhgViTwsYHtYcEXiQkHjz3jiOZY_ZlcZk&",
        //sourceIMGFinal:"",
        restaurant:[]
        //src="https://www.google.com/maps/embed/v1/view?key=AIzaSyDhgViTwsYHtYcEXiQkHjz3jiOZY_ZlcZk&"
      }
  },
  mounted() {
      console.log("Avant affichage, on pourra faire un fetch ici");
      console.log("ID = " + this.id)
      let url = "http://localhost:8080/api/restaurants/" + this.id;
      fetch(url)
        .then((response) => {
          return response.json();
        })
        .then((obj) => {
          console.log("caca2 = " + obj)
          this.restaurant = obj.restaurant
          console.log("sjdhgve = " + this.restaurant)
        });

  },
  methods: {
    recuperationCoordonnees(){
      var srcRestaurant="https://www.google.com/maps/embed/v1/view?key=AIzaSyDPwp2JOdBPZNAmB3g9K2YWXxsiVCvn5dg&" 
      const coordonnees = ""+this.restaurant.address.coord;
      var coordsplit = coordonnees.split(",");
      var longitude = coordsplit[1];
      var latitude = coordsplit[0];
      console.log("longitude = " + longitude + "latitude = " + latitude)

      return srcRestaurant+"center="+longitude+","+latitude+"&zoom=20&maptype=satellite"
    },
    recuCoordImage(){
      var srcImg = "https://maps.googleapis.com/maps/api/streetview?size=400x400"
      const coordonnees = ""+this.restaurant.address.coord;
      var coordsplit = coordonnees.split(",");
      var longitude = coordsplit[1];
      var latitude = coordsplit[0];
      return srcImg + "&location=" + longitude + "," + latitude + "&fov=80&heading=70&pitch=0&key=AIzaSyDPwp2JOdBPZNAmB3g9K2YWXxsiVCvn5dg"
    }

      
  }
}
</script>
<!--
<script async defer src="https://maps.googleapis.com/maps/api/js?key=AIzaSyDhgViTwsYHtYcEXiQkHjz3jiOZY_ZlcZk&callback=initMap"
  type="text/javascript"></script>
-->
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.mapRestau{width: 80%; height: 350px; display: inline-block;}
.styleMap{display: inline-block; width: 100%; height: inherit;}
</style>
