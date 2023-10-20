<template>
    <div>
        <h1>Create Philips</h1>
        <form v-on:submit.prevent="createPhilips">
            <p>ชื่อ: <input type="text" v-on="philips.name_thai"></p>
            <p>name: <input type="text" v-model="philips.name_eng"></p>
            <p>รุ่น: <input type="text" v-model="philips.model"></p>
            <p>ประเภท: <input type="text" v-model="philips.category"></p>
            <p>รายละเอียด: <input type="text" v-model="philips.detail"></p>
            <p>ราคา: <input type="text" v-model="philips.price"></p>
            <p><button type="submit">create philips</button></p>
        </form>
        <hr>
        <div>
            <p>ชื่อ: {{ philips.name_thai }}</p>
            <p>name: {{ philips.name_eng }}</p>
            <p>รุ่น: {{ philips.model }}</p>
            <p>ประเภท: {{ philips.category }}</p>
            <p>รายละเอียด: {{ philips.detail }}</p>
            <p>ราคา: {{ philips.price }}</p>
        </div>
    </div>
</template>
<script>
import PhilipsService from '@/services/PhilipsService'
export default {
    data() {
        return {
            philips: {
                name_thai: '',
                name_eng: '',
                model: '',
                category: '',
                detail: '',
                price: '',
            }
        }
    },
    methods: {
        async createPhilips() {
            try {
                await PhilipsService.post(this.philips)
                this.$router.push({
                    name: 'philipss'
                })
            } catch (err) {
                console.log(err)
            }
        }
    }
}
</script>
<style scoped></style>
   