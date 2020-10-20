<template>
  <div class="qa-container">
    <van-cell title="选择日期区间" :value="date" @click="show = true" />
    <van-calendar v-model="show" type="range" @confirm="onConfirm" />
    <van-calendar v-model="show" type="range" :formatter="formatter" />
  </div>
</template>

<script>
export default {
  name: 'QaIndex',
  components: {},
  props: {},
  data () {
    return {
      text: '',
      show: false,
    }
  },
  computed: {},
  watch: {},
  created () {},
  mounted () {},
  methods: {
    formatDate(date) {
      return `${date.getMonth() + 1}/${date.getDate()}`;
    },
    onConfirm(date) {
      const [start, end] = date;
      this.show = false;
      this.date = `${this.formatDate(start)} - ${this.formatDate(end)}`;
    },
    formatter(day) {
      const month = day.date.getMonth() + 1;
      const date = day.date.getDate();

      if (month === 5) {
        if (date === 1) {
          day.topInfo = '劳动节';
        } else if (date === 4) {
          day.topInfo = '青年节';
        } else if (date === 11) {
          day.text = '今天';
        }
      }

      if (day.type === 'start') {
        day.bottomInfo = '开始';
      } else if (day.type === 'end') {
        day.bottomInfo = '结束';
      }

      return day;
    },
  },

}
</script>

<style scoped lang="less"></style>
