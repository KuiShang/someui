<!--
 * @Author: shangkuikui
 * @Date: 2020-09-14 20:13:25
 * @LastEditTime: 2020-09-16 14:22:19
 * @LastEditors: shangkuikui
 * @FilePath: /someui/src/components/ExpandButton.vue
-->
<template>
  <div class="expand-button-wraper">
    <div class="content" :style="{ height: isHasExpand ? showheight : 'auto' }">
      <slot></slot>
    </div>
    <div class="education-content-more" @click="expandHandle">
      <span v-if="isHasExpand" class="expand-handle"
        >{{ expandtxt }}<span class="rearrow"></span
      ></span>
      <span v-else class="expand-handle"
        >{{ closetxt }}<span class="arrow"></span
      ></span>
    </div>
  </div>
</template>
<script>
export default {
  name: "ExpandButton",
  props: {
    showheight: {
      String,
      default: "0",
    },
    expandtxt: {
      String,
      default: "展开列表",
    },
    closetxt: {
      String,
      default: "收起列表",
    },
  },
  data() {
    return {
      isHasExpand: true,
    };
  },
  methods: {
    expandHandle(e) {
      this.isHasExpand = !this.isHasExpand;
      this.$emit("click", this.isHasExpand);
      e.stopPropagation();
    },
  },
};
</script>
<style lang="scss">
.expand-button-wraper {
  .content {
    overflow: hidden;
  }

  .arrow {
    height: 15px;
    width: 15px;
    display: inline-block;
    background-size: cover;
    background-image: url("../assets/education-arrow.png");
  }
  .rearrow {
    height: 15px;
    width: 15px;
    display: inline-block;
    background-size: cover;
    background-image: url("../assets/education-re-arrow.png");
  }
  .expand-handle {
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 15px;
    font-family: PingFangSC-Medium;
    color: #46648c;
    padding-top: 25px;
    border-top: 1px solid #e1e2e6;
    margin-top: 15px;
  }
}
</style>
