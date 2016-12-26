<template>
  <vue-timepicker v-model="time" @change="change" :minute-interval="10"></vue-timepicker>
</template>

<script>
  import VueTimepicker from 'vue2-timepicker'
  export default {
    watch: {
      value: {
        handler: function (val) {
          if (val) {
            this.time = val
          }
        },
        deep: true
      }
    },
    props: {
      value: {
        type: Object,
        requried: true
      }
    },
    components: {
      VueTimepicker
    },
    data: function () {
      return {
        time: {
          HH: '',
          mm: '',
          ss: ''
        }
      }
    },
    mounted: function () {
      this.$nextTick(function () {
        // code that assumes this.$el is in-document
      })
      this.time = this.value // value 已赋值好时，在这里同步
    },
    methods: {
      change: function (val) {
        let time = {}
        time.HH = val.data.HH
        time.mm = val.data.mm
        time.ss = val.data.ss
        if (time.HH === '' && time.mm === '') return // 初始化时不要影响到原数据
        this.$emit('input', time)
      }
    }
  }
</script>
