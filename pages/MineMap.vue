<template>
  <div :id="options.container" class="vue-minemap">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    name: "MineMap",
    data(){
return {

}
    },
    props: {
      accessToken: {
        type: String,
        required: true,
      },
      solution: {
        type: [String, Number],
        required: true,
      },
      options: {
        type: Object,
        required: true,
      },
      urls: {
        type: Object,
        required: false,
      }
    },

    mounted() {
      this.initMap()
    },
   
    methods: {
      initMap() {
        const minemap = minemap || window.minemap;
        const {accessToken, solution, options,urls} = this;
     
        minemap.accessToken = accessToken;
        minemap.solution = solution;
       
        this.map = new minemap.Map(options);
      
        this.map.on('load', () => {
          this.$emit('map-load', this.map);
         
        })
      },
     
    }
  }
</script>

<style scoped>
  .vue-minemap {
    height: 400px;
  }
</style>