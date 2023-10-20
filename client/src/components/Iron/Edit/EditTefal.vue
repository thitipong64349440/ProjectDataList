<template>
    <div>
        <h1>Edit Tefal</h1>
        <form v-on:submit.prevent="editTefal">
            <p>ชื่อ: <input type="text" v-model="tefal.name_thai"></p>
            <p>name: <input type="text" v-model="tefal.name_eng"></p>
            <p>รุ่น: <input type="text" v-model="tefal.model"></p>
            <p>ประเภท: <input type="text" v-model="tefal.category"></p>
            <p>รายละเอียด: <input type="text" v-model="tefal.detail"></p>
            <p><button type="submit">edit tefal</button></p>
        </form>
        <hr>
        <div>
            <p>ชื่อ: {{ tefal.name_thai }}</p>
            <p>name: {{ tefal.name_eng }}</p>
            <p>รุ่น: {{ tefal.model }}</p>
            <p>ประเภท: {{ tefal.category }}</p>
            <p>รายละเอียด: {{ tefal.detail }}</p>
            <p></p>
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
            }
        }
    },
    methods: {
        async editTefal() {
            try {
                await TefalService.put(this.tefal)
                this.$router.push({
                    name: 'tefals'
                })
            } catch (err) {
                console.log(err)
            }
        }
    },
    async created() {
        try {
            let tefalId = this.$route.params.tefalId
            this.tefal = (await TefalService.show(tefalId)).data
        } catch (error) {
            console.log(error)
        }
    }
}
</script>
<style scoped></style>