<template>
  <div>
    粉丝数：
    <p>国内网站:{{ fans | fansFormat('China') }}</p>
    <p>国外网站:{{ fans | fansFormat('Foreign') }}</p>

    时间是：
    <p>{{ new Date() | dateFormat('-') }}</p>
    <p>{{ new Date() | dateFormat('/') }}</p>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  data() {
    return {
      fans: 1876986,
    }
  },
  filters: {
    fansFormat(fans, val) {
      return val === 'China'
        ? (fans = fans / 10000 + '万')
        : (fans = fans / 1000 + '千')
    },
    dateFormat(time, val) {
      return moment(time).format('YYYY MM DD').replace(/\D/g, val)
    },
  },
}
</script>

<style></style>
