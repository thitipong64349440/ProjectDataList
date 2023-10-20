<template>
    <div>
        <h1>Create Tefal</h1>
        <form v-on:submit.prevent="createTefal">
            <p>ชื่อ: <input type="text" v-on="tefal.name_thai"></p>
            <p>name: <input type="text" v-model="tefal.name_eng"></p>
            <p>รุ่น: <input type="text" v-model="tefal.model"></p>
            <p>ประเภท: <input type="text" v-model="tefal.category"></p>
            <p>รายละเอียด: <input type="text" v-model="tefal.detail"></p>
            <p>ราคา: <input type="text" v-model="tefal.price"></p>
            <p><button type="submit">create tefal</button></p>
        </form>
        <hr>
        <div>
            <p>ชื่อ: {{ tefal.name_thai }}</p>
            <p>name: {{ tefal.name_eng }}</p>
            <p>รุ่น: {{ tefal.model }}</p>
            <p>ประเภท: {{ tefal.category }}</p>
            <p>รายละเอียด: {{ tefal.detail }}</p>
            <p>ราคา: {{ tefal.price }}</p>
        </div>
    </div>
</template>
<script>
import TefalService from '@/services/TefalService'
export default {
    data() {
        return {
            tefal: {
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
        async createTefal() {
            try {
                await TefalService.post(this.tefal)
                this.$router.push({
                    name: 'tefals'
                })
            } catch (err) {
                console.log(err)
            }
        }
    }
}
</script>
<style scoped></style>
   