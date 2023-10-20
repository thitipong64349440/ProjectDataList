<template>
  <div>
      <h1>Electrolux</h1>
      <p><button v-on:click="create">Create Electrolux</button></p>
      <div v-for="electrolux in electroluxs" v-bind:key="electrolux.id">
          <div>ชื่อ: {{ electrolux.name_thai }} {{ electrolux.name_eng }}</div>
          <div>รุ่น: {{ electrolux.model }}</div>
          <div>ราคา: {{ electrolux.price }}</div>
          <button v-on:click="navigateTo('/electrolux/' + electrolux.id)">ดูข้อมูลผู้ใช้</button>
          <button v-on:click="navigateTo('/electrolux/edit/' + electrolux.id)">แก้ไขข้อมูล</button>
          <button v-on:click="deleteElectrolux(electrolux)">ลบข้อมูล</button>
          <hr>
      </div>
  </div>
</template>
<script>
import ElectroluxService from '@/services/ElectroluxService'
export default {
  data() {
      return {
        electroluxs: []
      }
  },
  // แสดงข้อมูล
  async created() {
      this.electroluxs = (await ElectroluxService.index()).data
  },
  methods: {
      navigateTo(route) {
          this.$router.push(route)
      }
  },
  methods: {
      // เข้าหน้าสร้าง User ใหม่
      create() {
          this.$router.push({name: 'electrolux-create'})
      },
      navigateTo(route) {
          this.$router.push(route)
      },
      // ลบข้อมูล
      async deleteElectrolux(electrolux) {
          let result = confirm("want to delete?")
          if (result) {
              try {
                  await ElectroluxService.delete(electrolux)
                  this.refreshData()
              } catch (err) {
                  console.log(err)
              }
          }
      },
      async refreshData() {
          this.electroluxs = (await ElectroluxService.index()).data
      },
  },


  catch(error) {
      console.log(error)
  }
}
</script>
<style scoped></style>