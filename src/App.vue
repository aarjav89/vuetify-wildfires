<template>
  <v-app id="inspire">
    <v-navigation-drawer
        v-model="drawer"
        app
       >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            MENU
          </v-list-item-title>


        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
          dense
          nav
      >
        <v-list-item
            v-for="item in items"
            :key="item.title"
            :to="item.to"
            link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>


    <!-- TOP APP BAR CODE STARTS -->
    <v-app-bar
        app
        absolute
        color="#332940"
        elevate-on-scroll
        scroll-target="#scrolling-techniques-7"
    >
      <v-app-bar-nav-icon color="white" @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title class="text-capitalize mytitle">Aarjav's Wildfires Project</v-toolbar-title>



    </v-app-bar>
    <v-sheet
        id="scrolling-techniques-7"
        class="overflow-y-auto"
        max-height="600"
    >

    </v-sheet>
    <!-- TOP APP BAR CODE ENDS -->

    <v-main>
         <router-view> </router-view>
    </v-main>
  </v-app>
</template>

<script>

export default {

  data: () => ({
    drawer: null,
    items: [
      { title: 'WildFires', icon: 'mdi-fire', to: '/' },
      { title: 'About', icon: 'mdi-help-box', to: '/about' },
    ],
  }),
}
</script>

<style>

.mytitle{
 color:white;
}
</style>
