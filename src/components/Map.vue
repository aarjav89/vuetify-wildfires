<template>
  <div>

      <GmapMap
      :center="center"
      :zoom="7"
      class="map text-center"
      >

        <span v-for="(m, index) in eventData">
             <GmapMarker v-if="m.categories[0].id == wildFires_Id"
                  :key="index"
                  :position="checkLatLng(m.geometries[0].coordinates[1],m.geometries[0].coordinates[0])"
                  :clickable="true"
                  :draggable="true"
                  :icon="{ url: require('@/assets/fire.png')}"
                  @click="center=m.position"

             />

      </span>






      </GmapMap>
  </div>
</template>

<script>
import GMap from 'vue2-google-maps'
import axios from 'axios'

export default
{
  components:{
    GMap,

  },
  data(){
    return{
      markers:[],
      center: {
        lat: 42.3265,
        lng: -122.8756
      },
      eventData:[],
      wildFires_Id:8
    }
  },
  methods:{
    async loadMarkers(){
      //alert("called drawMarkers")

      await axios.get('https://eonet.sci.gsfc.nasa.gov/api/v2.1/events').then(
          response=>{
            this.eventData = response.data.events
             console.log(this.eventData);
          })

    },
    checkLatLng(latitude,longitude){
      //alert("latitude is : "+latitude)
      return {lat:latitude,lng:longitude}
    }
  },
  mounted(){
    this.loadMarkers()
  }

}
</script>

<style scoped>
.map {
  width: 100%;
  height: 800px;
  position: relative;
}

</style>
