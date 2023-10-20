<template>
    <div>
        <h1>Iron All brands</h1>
        <div>Tefal</div>
        <button v-on:click="navigateTo('/tefals')">ดูรายการ</button>
        <hr>
        <div>Philips</div>
        <button v-on:click="navigateTo('/philipss')">ดูรายการ</button>
        <hr>
        <div>Xiaomi</div>
        <button v-on:click="navigateTo('/xiaomis')">ดูรายการ</button>
        <hr>
        <div>Electrolux</div>
        <button v-on:click="navigateTo('/electroluxs')">ดูรายการ</button>
    </div>
</template>
<script>
import ElectroluxService from '@/services/ElectroluxService'
import PhilipsService from '@/services/PhilipsService'
import TefalService from '@/services/TefalService'
import XiaomiService from '@/services/XiaomiService'
export default {
  methods: {
      navigateTo(route) {
          this.$router.push(route)
      },
  },
}
</script>
<style scoped></style>
   