<template>
    <div>
        <h1>Tefal</h1>
        <div>id: {{ tefal.id }}</div>
        <div>ชื่อ: {{ tefal.name_thai }} {{ tefal.name_eng }}</div>
        <div>รุ่น: {{ tefal.model }}</div>
        <div>ประเภท: {{ tefal.category }}</div>
        <div>รายละเอียด: {{ tefal.detail }}</div>
        <div>ราคา: {{ tefal.price }}</div>
        <div><button v-on:click="navigateTo('/tefals')">กลับ</button></div>
        <hr>
    </div>
</template>
<script>
import TefalService from '@/services/TefalService'

export default {
    data() {
        return {
            tefal:null
        }
    },
    methods:{
        navigateTo(route){
            this.$router.push(route)
        }
    },
    async created() {
        try{
            let tefalId = this.$route.params.tefalId
            this.tefal = (await TefalService.show(tefalId)).data
            console.log(this.tefal)
        }catch (err) {
            console.log (err)
        }
    }
}
</script>
<style scoped>
</style>
   