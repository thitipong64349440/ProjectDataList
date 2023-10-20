<template>
    <div>
        <h1>Edit Philips</h1>
        <form v-on:submit.prevent="editPhilips">
            <p>ชื่อ: <input type="text" v-model="philips.name_thai"></p>
            <p>name: <input type="text" v-model="philips.name_eng"></p>
            <p>รุ่น: <input type="text" v-model="philips.model"></p>
            <p>ประเภท: <input type="text" v-model="philips.category"></p>
            <p>รายละเอียด: <input type="text" v-model="philips.detail"></p>
            <p><button type="submit">edit philips</button></p>
        </form>
        <hr>
        <div>
            <p>ชื่อ: {{ philips.name_thai }}</p>
            <p>name: {{ philips.name_eng }}</p>
            <p>รุ่น: {{ philips.model }}</p>
            <p>ประเภท: {{ philips.category }}</p>
            <p>รายละเอียด: {{ philips.detail }}</p>
            <p></p>
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
            }
        }
    },
    methods: {
        async editPhilips() {
            try {
                await PhilipsService.put(this.philips)
                this.$router.push({
                    name: 'philipss'
                })
            } catch (err) {
                console.log(err)
            }
        }
    },
    async created() {
        try {
            let philipsId = this.$route.params.philipsId
            this.philips = (await PhilipsService.show(philipsId)).data
        } catch (error) {
            console.log(error)
        }
    }
}
</script>
<style scoped></style>