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
      worldName:["Gaia","Alexander","Bahamut","Durandal","Fenrir","Ifrit","Ridill","Tiamat","Ultima","Valefor","Yojimbo","Zeromus"],
    }
  },
  
}


</script>
