<template>
  <div>    
        <Item 
         :worlds = "worldName"
        >
        </Item> 

  <Footer class="mb-14"/>
  
  <Nav />

  </div>
</template>

<script>
import Footer from '~/components/footer.vue';
import Item from '~/components/item.vue';

export default {
  components: {
    Footer: Footer,
    Item: Item
  },
  layout:"market",
  data() {
    return {
      worldName:["Elemental","Aegis","Atomos","Carbuncle","Garuda","Gungnir","Kujata","Ramuh","Tonberry","Typhon","Unicorn"],
    }
  },
  
}


</script>
