<template>
  <div>
    <h3>粉丝数量</h3>
    <p>国内网站：粉丝数量：{{ fans | fans('domestic') }}万</p>
    <p>外国网站：粉丝数量：{{ fans | fans('theUSA') }}千</p>
    <h3>时间</h3>
    <span>时间：{{ firstTime | times('-') }}</span> <br />
    <span>时间：{{ firstTime | times('/') }}</span>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  data() {
    return {
      fans: 1876986,
      firstTime: 1636450540055,
    }
  },
  filters: {
    fans(fans, val) {
      return val === 'domestic' ? (fans = fans / 10000) : (fans = fans / 1000)
    },
    times(firstTime,val) {
      return moment(firstTime).format('YYYY-MM-DD').replace(/\D/g,val)
    },
  },
}
</script>

<style></style>
