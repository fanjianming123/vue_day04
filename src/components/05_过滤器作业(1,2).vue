<template>
  <div>
    国内网站：粉丝数量{{ beauty | girls }} <br />
    国内网站：粉丝数量{{ beauty | girlplus }}
    时间：{{ ugly | boys }} <br />
    时间：{{ ugly | boyplus }}
  </div>
</template>

<script>
import moment from 'moment'
export default {
  data() {
    return {
      beauty: '1876986',
      ugly: +new Date(),
    }
  },
  filters: {
    girls(val) {
      return val / 10000 + '万'
    },
    girlplus(val) {
      return val / 1000 + '千'
    },
    boys(val) {
      return moment(val).format('YYYY-MM-DD')
    },
    boyplus(val) {
      return moment(val).format('YYYY/MM/DD')
    },
  },
}
</script>

<style></style>
