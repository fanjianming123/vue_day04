<template>
  <div>
    国内网站：粉丝数量{{ beauty | girls }} <br>
    国内网站：粉丝数量{{ beauty | girlplus }}
  </div>
</template>

<script>
export default {
  data() {
    return {
      beauty: '1876986',
    }
  },
  filters: {
    girls(val) {
      return val / 10000 + '万'
    },
    girlplus(val) {
      return val / 1000 + '千'
    },
  },
}
</script>

<style></style>
