<template>
    <div>
        <h1>Create Electrolux</h1>
        <form v-on:submit.prevent="createElectrolux">
            <p>ชื่อ: <input type="text" v-on="electrolux.name_thai"></p>
            <p>name: <input type="text" v-model="electrolux.name_eng"></p>
            <p>รุ่น: <input type="text" v-model="electrolux.model"></p>
            <p>ประเภท: <input type="text" v-model="electrolux.category"></p>
            <p>รายละเอียด: <input type="text" v-model="electrolux.detail"></p>
            <p>ราคา: <input type="text" v-model="electrolux.price"></p>
            <p><button type="submit">create electrolux</button></p>
        </form>
        <hr>
        <div>
            <p>ชื่อ: {{ electrolux.name_thai }}</p>
            <p>name: {{ electrolux.name_eng }}</p>
            <p>รุ่น: {{ electrolux.model }}</p>
            <p>ประเภท: {{ electrolux.category }}</p>
            <p>รายละเอียด: {{ electrolux.detail }}</p>
            <p>ราคา: {{ electrolux.price }}</p>
        </div>
    </div>
</template>
<script>
import ElectroluxService from '@/services/ElectroluxService'
export default {
    data() {
        return {
            electrolux: {
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
        async createElectrolux() {
            try {
                await ElectroluxService.post(this.electrolux)
                this.$router.push({
                    name: 'electroluxs'
                })
            } catch (err) {
                console.log(err)
            }
        }
    }
}
</script>
<style scoped></style>
   