<template>
  <v-expansion-panels focusable class="py-8 mt-16 mx-md-auto" style="width:960px;">
    <v-expansion-panel v-for="(price , i) in prices" :key="price.id">
      
      <v-expansion-panel-header>
        <v-img :src="lists[i].img" max-height="40" max-width="40" class="mr-5"></v-img>
        <span class="blue--text text--lighten-2 font-weight-bold">{{ lists[i].name }}</span>
      </v-expansion-panel-header>
      
      <v-expansion-panel-content>
        
        <v-simple-table dense class="grey darken-3 mt-4">
            <thead>
                <tr>
                  <th class="text-left">Server</th>
                  <th class="text-left" v-for="index in 10" :key="index">{{ "# " + index }}</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="(pri, j) in price" :key="pri.id">
                  <td v-if="j < worlds.length - 1">{{ worlds[j + 1] }}</td>
                  <td v-if="j < worlds.length - 1">{{ pri[0] }}</td>
                  <td v-if="j < worlds.length - 1">{{ pri[1] }}</td>
                  <td v-if="j < worlds.length - 1">{{ pri[2] }}</td>
                  <td v-if="j < worlds.length - 1">{{ pri[3] }}</td>
                  <td v-if="j < worlds.length - 1">{{ pri[4] }}</td>
                  <td v-if="j < worlds.length - 1">{{ pri[5] }}</td>
                  <td v-if="j < worlds.length - 1">{{ pri[6] }}</td>
                  <td v-if="j < worlds.length - 1">{{ pri[7] }}</td>
                  <td v-if="j < worlds.length - 1">{{ pri[8] }}</td>
                  <td v-if="j < worlds.length - 1">{{ pri[9] }}</td>
                </tr>
              </tbody>
          </v-simple-table>

      </v-expansion-panel-content>

    </v-expansion-panel>
  </v-expansion-panels>
</template>

<script>
import axios from 'axios';

export default {
  props:{
    worlds : {
      type: Array,
      required: true,
      default: {}
    }
  },
  data () {
    return {
      lists: [
        {img:"image/a1.webp",name:"武略のマテリア",code:"5669"},
        {img:"image/a2.webp",name:"武略のマテリラ",code:"5670"},
        {img:"image/a3.webp",name:"武略のマテリダ",code:"5671"},
        {img:"image/a4.webp",name:"武略のマテリガ",code:"5672"},
        {img:"image/a5.webp",name:"武略のマテリジャ",code:"5673"},
        {img:"image/a6.webp",name:"武略のハイマテリジャ",code:"18019"},
        {img:"image/a7.webp",name:"武略のメガマテリジャ",code:"25188"},
        {img:"image/a8.webp",name:"武略のエクスマテリジャ",code:"26729"},

        {img:"image/a1.webp",name:"雄略のマテリア",code:"5674"},
        {img:"image/a2.webp",name:"雄略のマテリラ",code:"5675"},
        {img:"image/a3.webp",name:"雄略のマテリダ",code:"5676"},
        {img:"image/a4.webp",name:"雄略のマテリガ",code:"5677"},
        {img:"image/a5.webp",name:"雄略のマテリジャ",code:"5678"},
        {img:"image/a6.webp",name:"雄略のハイマテリジャ",code:"18020"},
        {img:"image/a7.webp",name:"雄略のメガマテリジャ",code:"25189"},
        {img:"image/a8.webp",name:"雄略のエクスマテリジャ",code:"26730"},

        {img:"image/a1.webp",name:"天眼のマテリア",code:"5664"},
        {img:"image/a2.webp",name:"天眼のマテリラ",code:"5665"},
        {img:"image/a3.webp",name:"天眼のマテリダ",code:"5666"},
        {img:"image/a4.webp",name:"天眼のマテリガ",code:"5667"},
        {img:"image/a5.webp",name:"天眼のマテリジャ",code:"5668"},
        {img:"image/a6.webp",name:"天眼のハイマテリジャ",code:"18018"},
        {img:"image/a7.webp",name:"天眼のメガマテリジャ",code:"25187"},
        {img:"image/a8.webp",name:"天眼のエクスマテリジャ",code:"26728"},

        {img:"image/b1.webp",name:"戦技のマテリア",code:"5714"},
        {img:"image/b2.webp",name:"戦技のマテリラ",code:"5715"},
        {img:"image/b3.webp",name:"戦技のマテリダ",code:"5716"},
        {img:"image/b4.webp",name:"戦技のマテリガ",code:"5717"},
        {img:"image/b5.webp",name:"戦技のマテリジャ",code:"5718"},
        {img:"image/b6.webp",name:"戦技のハイマテリジャ",code:"18028"},
        {img:"image/b7.webp",name:"戦技のメガマテリジャ",code:"25197"},
        {img:"image/b8.webp",name:"戦技のエクスマテリジャ",code:"26738"},

        {img:"image/b1.webp",name:"詠唱のマテリア",code:"5719"},
        {img:"image/b2.webp",name:"詠唱のマテリラ",code:"5720"},
        {img:"image/b3.webp",name:"詠唱のマテリダ",code:"5721"},
        {img:"image/b4.webp",name:"詠唱のマテリガ",code:"5722"},
        {img:"image/b5.webp",name:"詠唱のマテリジャ",code:"5723"},
        {img:"image/b6.webp",name:"詠唱のハイマテリジャ",code:"18029"},
        {img:"image/b7.webp",name:"詠唱のメガマテリジャ",code:"25198"},
        {img:"image/b8.webp",name:"詠唱のエクスマテリジャ",code:"26739"},

        {img:"image/c1.webp",name:"剛柔のマテリア",code:"5679"},
        {img:"image/c2.webp",name:"剛柔のマテリラ",code:"5680"},
        {img:"image/c3.webp",name:"剛柔のマテリダ",code:"5681"},
        {img:"image/c4.webp",name:"剛柔のマテリガ",code:"5682"},
        {img:"image/c5.webp",name:"剛柔のマテリジャ",code:"5683"},
        {img:"image/c6.webp",name:"剛柔のハイマテリジャ",code:"18021"},
        {img:"image/c7.webp",name:"剛柔のメガマテリジャ",code:"25190"},
        {img:"image/c8.webp",name:"剛柔のエクスマテリジャ",code:"26731"},

        {img:"image/c1.webp",name:"信力のマテリア",code:"5629"},
        {img:"image/c2.webp",name:"信力のマテリラ",code:"5630"},
        {img:"image/c3.webp",name:"信力のマテリダ",code:"5631"},
        {img:"image/c4.webp",name:"信力のマテリガ",code:"5632"},
        {img:"image/c5.webp",name:"信力のマテリジャ",code:"5633"},
        {img:"image/c6.webp",name:"信力のハイマテリジャ",code:"18011"},
        {img:"image/c7.webp",name:"信力のメガマテリジャ",code:"25186"},
        {img:"image/c8.webp",name:"信力のエクスマテリジャ",code:"26727"},

        {img:"image/d1.webp",name:"達識のマテリア",code:"5684"},
        {img:"image/d2.webp",name:"達識のマテリラ",code:"5685"},
        {img:"image/d3.webp",name:"達識のマテリダ",code:"5686"},
        {img:"image/d4.webp",name:"達識のマテリガ",code:"5687"},
        {img:"image/d5.webp",name:"達識のマテリジャ",code:"5688"},
        {img:"image/d6.webp",name:"達識のハイマテリジャ",code:"18022"},
        {img:"image/d7.webp",name:"達識のメガマテリジャ",code:"25191"},
        {img:"image/d8.webp",name:"達識のエクスマテリジャ",code:"26732"},

        {img:"image/d1.webp",name:"博識のマテリア",code:"5689"},
        {img:"image/d2.webp",name:"博識のマテリラ",code:"5690"},
        {img:"image/d3.webp",name:"博識のマテリダ",code:"5691"},
        {img:"image/d4.webp",name:"博識のマテリガ",code:"5692"},
        {img:"image/d5.webp",name:"博識のマテリジャ",code:"5693"},
        {img:"image/d6.webp",name:"博識のハイマテリジャ",code:"18023"},
        {img:"image/d7.webp",name:"博識のメガマテリジャ",code:"25192"},
        {img:"image/d8.webp",name:"博識のエクスマテリジャ",code:"26733"},

        {img:"image/d1.webp",name:"器識のマテリア",code:"5694"},
        {img:"image/d2.webp",name:"器識のマテリラ",code:"5695"},
        {img:"image/d3.webp",name:"器識のマテリダ",code:"5696"},
        {img:"image/d4.webp",name:"器識のマテリガ",code:"5697"},
        {img:"image/d5.webp",name:"器識のマテリジャ",code:"5698"},
        {img:"image/d6.webp",name:"器識のハイマテリジャ",code:"18024"},
        {img:"image/d7.webp",name:"器識のメガマテリジャ",code:"25193"},
        {img:"image/d8.webp",name:"器識のエクスマテリジャ",code:"26734"},

        {img:"image/e1.webp",name:"名匠のマテリア",code:"5699"},
        {img:"image/e2.webp",name:"名匠のマテリラ",code:"5700"},
        {img:"image/e3.webp",name:"名匠のマテリダ",code:"5701"},
        {img:"image/e4.webp",name:"名匠のマテリガ",code:"5702"},
        {img:"image/e5.webp",name:"名匠のマテリジャ",code:"5703"},
        {img:"image/e6.webp",name:"名匠のハイマテリジャ",code:"18025"},
        {img:"image/e7.webp",name:"名匠のメガマテリジャ",code:"25194"},
        {img:"image/e8.webp",name:"名匠のエクスマテリジャ",code:"26735"},

        {img:"image/e1.webp",name:"魔匠のマテリア",code:"5704"},
        {img:"image/e2.webp",name:"魔匠のマテリラ",code:"5705"},
        {img:"image/e3.webp",name:"魔匠のマテリダ",code:"5706"},
        {img:"image/e4.webp",name:"魔匠のマテリガ",code:"5707"},
        {img:"image/e5.webp",name:"魔匠のマテリジャ",code:"5708"},
        {img:"image/e6.webp",name:"魔匠のハイマテリジャ",code:"18026"},
        {img:"image/e7.webp",name:"魔匠のメガマテリジャ",code:"25195"},
        {img:"image/e8.webp",name:"魔匠のエクスマテリジャ",code:"26736"},

        {img:"image/e1.webp",name:"巨匠のマテリア",code:"5709"},
        {img:"image/e2.webp",name:"巨匠のマテリラ",code:"5710"},
        {img:"image/e3.webp",name:"巨匠のマテリダ",code:"5711"},
        {img:"image/e4.webp",name:"巨匠のマテリガ",code:"5712"},
        {img:"image/e5.webp",name:"巨匠のマテリジャ",code:"5713"},
        {img:"image/e6.webp",name:"巨匠のハイマテリジャ",code:"18027"},
        {img:"image/e7.webp",name:"巨匠のメガマテリジャ",code:"25196"},
        {img:"image/e8.webp",name:"巨匠のエクスマテリジャ",code:"26737"},

      ],
      codes:[""],
      prices:[]
    }
  },
  created() {
    this.prices.splice(0)
    
    for (let i = 0; i < this.lists.length; i++) {
      // 配列の追加   
      this.$set(this.prices, i, [])
      for (let j = 0; j < this.worlds.length; j++) {
        // 配列の追加
        this.$set(this.prices[i], j, [])
      }

        axios.get('https://universalis.app/api/' + this.worlds[0] + '/' +this.lists[i].code)
          .then((response) => {
          let item_price = response.data.listings
          for (let k = 0; k < item_price.length; k++) {

            for (let index = 0; index < this.worlds.length; index++) {
              if(this.worlds[index + 1] == item_price[k].worldName){
                this.prices[i][index].push(item_price[k].pricePerUnit)
                break
              }
            }
          }

        })
        
        .catch(err => {
          console.log("error")
          console.log(err)
        })
        //error処理
    }
  },
}
</script>