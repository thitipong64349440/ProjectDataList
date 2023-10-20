<template>
    <div>
        <h1>Edit Electrolux</h1>
        <form v-on:submit.prevent="editElectrolux">
            <p>ชื่อ: <input type="text" v-model="electrolux.name_thai"></p>
            <p>name: <input type="text" v-model="electrolux.name_eng"></p>
            <p>รุ่น: <input type="text" v-model="electrolux.model"></p>
            <p>ประเภท: <input type="text" v-model="electrolux.category"></p>
            <p>รายละเอียด: <input type="text" v-model="electrolux.detail"></p>
            <p><button type="submit">edit electrolux</button></p>
        </form>
        <hr>
        <div>
            <p>ชื่อ: {{ electrolux.name_thai }}</p>
            <p>name: {{ electrolux.name_eng }}</p>
            <p>รุ่น: {{ electrolux.model }}</p>
            <p>ประเภท: {{ electrolux.category }}</p>
            <p>รายละเอียด: {{ electrolux.detail }}</p>
            <p></p>
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
            }
        }
    },
    methods: {
        async editElectrolux() {
            try {
                await ElectroluxService.put(this.electrolux)
                this.$router.push({
                    name: 'electroluxs'
                })
            } catch (err) {
                console.log(err)
            }
        }
    },
    async created() {
        try {
            let electroluxId = this.$route.params.electroluxId
            this.electrolux = (await ElectroluxService.show(electroluxId)).data
        } catch (error) {
            console.log(error)
        }
    }
}
</script>
<style scoped></style>