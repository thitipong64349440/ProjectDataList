<template>
    <div>
        <h1>Philips</h1>
        <div>id: {{ philips.id }}</div>
        <div>ชื่อ: {{ philips.name_thai }} {{ philips.name_eng }}</div>
        <div>รุ่น: {{ philips.model }}</div>
        <div>ประเภท: {{ philips.category }}</div>
        <div>รายละเอียด: {{ philips.detail }}</div>
        <div>ราคา: {{ philips.price }}</div>
        <div><button v-on:click="navigateTo('/philipss')">กลับ</button></div>
        <hr>
    </div>
</template>
<script>
import PhilipsService from '@/services/PhilipsService'

export default {
    data() {
        return {
            philips:null
        }
    },
    methods:{
        navigateTo(route){
            this.$router.push(route)
        }
    },
    async created() {
        try{
            let philipsId = this.$route.params.philipsId
            this.philips = (await PhilipsService.show(philipsId)).data
            console.log(this.philips)
        }catch (err) {
            console.log (err)
        }
    }
}
</script>
<style scoped>
</style>
   