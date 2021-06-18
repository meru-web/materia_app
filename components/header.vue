<template>
  
    <v-app-bar color="primary" dark app >
      <v-toolbar-title>FFXIV<br>Materia_Price</v-toolbar-title>
      <v-row>
        
        <v-col class="d-flex flex-row-reverse">
          <v-btn color="grey lighten-5" rounded depressed class="ml-1">
            <nuxt-link to="/elemental" color="primary" style="text-decoration: none; font-weight:bold;">
            <v-icon color="primary">mdi-cart</v-icon>
            MARKET
            </nuxt-link>
          </v-btn>
        </v-col>

      </v-row>
    </v-app-bar>
</template>

<script>
export default {}
</script>