<template>
  <div class="video-container">
    <van-dropdown-menu active-color="rgb(0,197,142)">
      <van-dropdown-item v-model="value" :options="option" />
      <van-dropdown-item title="筛选" ref="item">
        <van-cell center title="4k">
          <template #right-icon>
            <van-switch v-model="switch1" size="24" active-color="rgb(0,197,142)" />
          </template>
        </van-cell>
        <van-cell center title="1080p">
          <template #right-icon>
            <van-switch v-model="switch2" size="24" active-color="rgb(0,197,142)" />
          </template>
        </van-cell>
        <div style="padding: 5px 16px; ">
          <van-button type="danger" block round @click="onConfirm" active-color="rgb(0,197,142)">
            确认
          </van-button>
        </div>
      </van-dropdown-item>
    </van-dropdown-menu>
  </div>
</template>

<script>
export default {
  name: 'VideoIndex',
  components: {},
  props: {},
  data () {
    return {value: 0,
      switch1: false,
      switch2: false,
      option: [
        { text: '推荐', value: 0 },
        { text: '热门直击', value: 1 },
        { text: '频道分类', value: 2 },
      ],}
  },
  computed: {},
  watch: {},
  created () {},
  mounted () {},
  methods: {onConfirm() {
      this.$refs.item.toggle();
    },
  }
}
</script>

<style scoped lang="less"></style>
