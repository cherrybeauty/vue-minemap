<template>
  <MineMap   v-bind="mapProps" @map-load='mapLoad'></MineMap>
</template>

<script lang="ts">
import Vue from 'vue'
 import MineMap from './MineMap'
export default Vue.extend({
  name: 'IndexPage',
   components:{
      MineMap,
    },
    data(){
      return  {
      map:null,
        mapProps: {
          accessToken: '16be596e00c44c86bb1569cb53424dc9',
          solution: '12877',
          options: {
            container: 'map',
            style: `//minedata.cn/service/solu/style/id/12877`,
            center: [116.1866179, 39.992559],
            zoom: 9,
            minZoom: 3,
            maxZoom: 17,
          }
        }
      }
    },
    methods:{
      mapLoad(map){
this.map=map;
      }
    }
})

</script>
