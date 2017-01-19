<template>
  <div>
    <doc :name="name"
      :desc="desc"
      :parm_desc="parm_desc"
      :parms="parms"
      :code="code"
      >
      <bz hide_clear_button v-model="time" ></bz>
    </doc>
  </div>
</template>
<script>
  // import toastr from 'toastr'

  import Bz from './Bz'
  import Doc from 'bz-doc'
  export default {
    components: {
      Bz,
      Doc
    },
    data: function () {
      return {
        time: null,
        name: 'bz-timepicer',
        desc: '登录页面',
        parms: [
          {parm: 'v-model', desc: '绑定时间'},
          {parm: 'hide_clear_button', desc: '隐藏清除按钮(只要有就生效)'}
        ],
        parm_desc: ``,
        code: `<bz hide_clear_button v-model="time" ></bz>`
      }
    },
    methods: {
      call_back: function (user_name, password) {
        this.loading = true
        let _this = this
        window.setTimeout(function () {
          window.alert(`user_name:${user_name}, password: ${password}`)
          // toastr.info('登录成功')
          _this.loading = false
        }, 2000)
      }
    }
  }
</script>
