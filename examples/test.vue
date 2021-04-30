<template>
  <div class="q-pa-md">
    <q-table
      v-if="data.lenth>0"
      title="Treats"
      :data="data"
      :columns="columns"
      row-key="name"
    />
    <button @click="handleFetch()"></button>
  </div>
</template>

<script>
import data from './data'
export default {
    mounted(){
        
    },
    data:function(){
        return{
            data:[],
        }
    },
    methods:{
        handleFetch(){
        this.$q.loading.show()
        fetch('http://0.0.0.0:6080/price_optimization_results/all').then((res)=>{
                    this.data = res;
                    this.$q.loading.hide()
                }).catch((err)=>{
                    console.log(err)
                    this.$q.loading.hide()
                })
        }
    },
}
</script>

<style lang="scss" scoped>

</style>