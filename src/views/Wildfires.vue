<template>
  <div class="pa-6">
   <Header/>

    <Map/>

  </div>
</template>

<script>
// @ is an alias to /src
import Map from '@/components/Map'
import Header from "@/components/Header";

export default {
  name: 'Home',
  components: {
    Map,
    Header
  }
}
</script>
