<template>
    <div>
        <h1>Electrolux</h1>
        <div>id: {{ electrolux.id }}</div>
        <div>ชื่อ: {{ electrolux.name_thai }} {{ electrolux.name_eng }}</div>        <div>รุ่น: {{ electrolux.model }}</div>
        <div>ประเภท: {{ electrolux.category }}</div>
        <div>รายละเอียด: {{ electrolux.detail }}</div>
        <div>ราคา: {{ electrolux.price }}</div>
        <div><button v-on:click="navigateTo('/electroluxs')">กลับ</button></div>
        <hr>
    </div>
</template>
<script>
import ElectroluxService from '@/services/ElectroluxService'

export default {
    data() {
        return {
            electrolux:null
        }
    },
    methods:{
        navigateTo(route){
            this.$router.push(route)
        }
    },
    async created() {
        try{
            let electroluxId = this.$route.params.electroluxId
            this.electrolux = (await ElectroluxService.show(electroluxId)).data
            console.log(this.electrolux)
        }catch (err) {
            console.log (err)
        }
    }
}
</script>
<style scoped>
</style>
   