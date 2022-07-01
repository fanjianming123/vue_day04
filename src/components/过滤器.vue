<template>
  <div>
    <div>
      国内网站:粉丝数量：{{ fans | kiss }} <br />
      外国网站:粉丝数量：{{ fans | kisss }}
    </div>
    <div>
      {{time | times }} <br>
      {{time | timess }}
    </div>
  </div>
</template>

<script>
import moment from 'moment';
export default {
  data() {
    return {
      fans: '1876986',
      time: +new Date()
    };
  },
  filters: {
    kiss(val) {
      return val / 10000 + '万';
    },
    kisss(val) {
      return val / 1000 + '千';
    },
    times(val){
      return moment(val).format('YYYY-MM-DD')
    },
    timess(val){
      return moment(val).format('YYYY/MM/DD')
    }
  },
};
</script>

<style></style>
