<template>
  <div class="tab-bar-class" @click="itemclick">
    <div v-if="!isActive"><slot name="item-icon"></slot></div>
    <div v-else><slot name="item-icon-active"></slot></div>
    <div :style="activeStyle"><slot name="item-text"></slot></div>
  </div>
</template>

<script>
export default {
  name:'TabBarItem',
  props:{
    path:String,
    activeColor:{
      type:String,
      default:'red'

    }
  },
  data() {
    return {
    
    }
  },
  computed: {
    isActive(){
      return this.$route.path.indexOf(this.path) != -1
    },
    activeStyle(){
      return this.isActive?{color:this.activeColor} : {}
    }

    
  },
  methods: {
    itemclick(){
      this.$router.replace({path:this.path},(onComplete) => {},
        (onAbort) => {})
    }
  }
}

</script>
<style scoped>
.tab-bar-class{
  flex: 1;
  text-align: center;
  /* 49px时用户使用最舒服的高度 */
  height: 49px;
}
.tab-bar-class img
{
  width: 24px;
  height: 24px;
  margin-top: 3px;
  vertical-align: middle;
  margin-bottom: 2px;

</style>