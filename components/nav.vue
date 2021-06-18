<template>

  <v-bottom-navigation
    color="light-blue"
    fixed
    grow
  >
  
    <v-btn
        v-for="link in links"
        :key="link.text" 
        :value="link.no"
        nuxt
        :to="link.path" 
        style="text-decoration: none; font-weight:bold;"
    >
          <span>{{ link.text }}</span>
          <v-icon>mdi-cards-diamond</v-icon>
    </v-btn>

  </v-bottom-navigation>

</template>

<script>
export default {
  data(){
    return{
      links:[
        { no:0, text:"Elemental", path:'/elemental'},
        { no:1, text:"Gaia", path:'/gaia'},
        { no:2, text:"Mana", path:'/mana'}
      ]
    }
  }
}
</script>