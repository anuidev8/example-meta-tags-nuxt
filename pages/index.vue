<template>
<div>
  <div v-if="!loading">
  <CompExample/>

  </div>
    <div v-if="loading">
    <h3>loading...</h3>
  </div>


</div>
</template>

<script>

export default {
  name: 'IndexPage',
  components:{
    CompExample : () => import('@/components/Compon')
  },
   data(){
    return{
      loading:true
    }
  },
    mounted() {

      this.loading = true
       document.addEventListener("DOMContentLoaded", () => {

    this.loading = false
  });


  }
}
</script>
