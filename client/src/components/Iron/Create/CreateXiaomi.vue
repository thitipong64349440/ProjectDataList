<template>
    <div>
        <h1>Create Xiaomi</h1>
        <form v-on:submit.prevent="createXiaomi">
            <p>ชื่อ: <input type="text" v-on="xiaomi.name_thai"></p>
            <p>name: <input type="text" v-model="texiaomifal.name_eng"></p>
            <p>รุ่น: <input type="text" v-model="xiaomi.model"></p>
            <p>ประเภท: <input type="text" v-model="xiaomi.category"></p>
            <p>รายละเอียด: <input type="text" v-model="xiaomi.detail"></p>
            <p>ราคา: <input type="text" v-model="xiaomi.price"></p>
            <p><button type="submit">create xiaomi</button></p>
        </form>
        <hr>
        <div>
            <p>ชื่อ: {{ xiaomi.name_thai }}</p>
            <p>name: {{ xiaomi.name_eng }}</p>
            <p>รุ่น: {{ xiaomi.model }}</p>
            <p>ประเภท: {{ xiaomi.category }}</p>
            <p>รายละเอียด: {{ xiaomi.detail }}</p>
            <p>ราคา: {{ xiaomi.price }}</p>
        </div>
    </div>
</template>
<script>
import XiaomiService from '@/services/XiaomiService'
export default {
    data() {
        return {
            xiaomi: {
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
        async createXiaomi() {
            try {
                await XiaomiService.post(this.xiaomi)
                this.$router.push({
                    name: 'xiaomis'
                })
            } catch (err) {
                console.log(err)
            }
        }
    }
}
</script>
<style scoped></style>
   