<template>
    <div>
        <h1>Edit Xiaomi</h1>
        <form v-on:submit.prevent="editXiaomi">
            <p>ชื่อ: <input type="text" v-model="xiaomi.name_thai"></p>
            <p>name: <input type="text" v-model="xiaomi.name_eng"></p>
            <p>รุ่น: <input type="text" v-model="xiaomi.model"></p>
            <p>ประเภท: <input type="text" v-model="xiaomi.category"></p>
            <p>รายละเอียด: <input type="text" v-model="xiaomi.detail"></p>
            <p><button type="submit">edit xiaomi</button></p>
        </form>
        <hr>
        <div>
            <p>ชื่อ: {{ xiaomi.name_thai }}</p>
            <p>name: {{ xiaomi.name_eng }}</p>
            <p>รุ่น: {{ xiaomi.model }}</p>
            <p>ประเภท: {{ xiaomi.category }}</p>
            <p>รายละเอียด: {{ xiaomi.detail }}</p>
            <p></p>
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
            }
        }
    },
    methods: {
        async editXiaomi() {
            try {
                await XiaomiService.put(this.xiaomi)
                this.$router.push({
                    name: 'xiaomis'
                })
            } catch (err) {
                console.log(err)
            }
        }
    },
    async created() {
        try {
            let xiaomiId = this.$route.params.xiaomiId
            this.xiaomi = (await XiaomiService.show(xiaomiId)).data
        } catch (error) {
            console.log(error)
        }
    }
}
</script>
<style scoped></style>