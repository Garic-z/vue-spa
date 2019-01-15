<template>
  <div class="home">
    code:{{result.code}}
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'home',
  components: {
  },
  data() {
    return {
      result: '',
      error:''
    }
  },
  created() {
    const that = this
    console.log(this.$route.params)
    var corpId = this.$route.params.corpId
    // ding46bc486401a6b2a135c2f4657eb6378f
    dd.ready(function(){
      dd.runtime.permission.requestAuthCode({
        corpId: corpId,
        onSuccess: function(result) {
          that.result = result
        },
        onFail : function(err) {
          that.error = err
          console.log(err)
        }
      })
    });
  },
}
</script>
