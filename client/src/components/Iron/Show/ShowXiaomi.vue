<template>
    <div>
        <h1>Xiaomi</h1>
        <div>id: {{ xiaomi.id }}</div>
        <div>ชื่อ: {{ xiaomi.name_thai }} {{ xiaomi.name_eng }}</div>
        <div>รุ่น: {{ xiaomi.model }}</div>
        <div>ประเภท: {{ xiaomi.category }}</div>
        <div>รายละเอียด: {{ xiaomi.detail }}</div>
        <div>ราคา: {{ xiaomi.price }}</div>
        <div><button v-on:click="navigateTo('/xiaomis')">กลับ</button></div>
        <hr>
    </div>
</template>
<script>
import XiaomiService from '@/services/XiaomiService'

export default {
    data() {
        return {
            xiaomi:null
        }
    },
    methods:{
        navigateTo(route){
            this.$router.push(route)
        }
    },
    async created() {
        try{
            let xiaomiId = this.$route.params.xiaomiId
            this.xiaomi = (await XiaomiService.show(xiaomiId)).data
            console.log(this.xiaomi)
        }catch (err) {
            console.log (err)
        }
    }
}
</script>
<style scoped>
</style>
   