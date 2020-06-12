<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive">
       <slot name="item-icon"></slot>
    </div>
    <div v-else>
       <slot name="item-icon-active"></slot>
    </div>  
    <div :style="activeStyle">
      <slot name="item-text"></slot>
    </div> 
    
  </div>
</template>

<script>
export default {
  name: "TabBarItem",
  props: {
    path : String,
    activeColor: {
      type: String,
      default: 'deeppink'
    }
  },
  methods: {
    itemClick() {
      this.$router.push(this.path).catch(err=>err)
    }
  },
  computed: {
    isActive() {
      return this.$route.path.indexOf(this.path) !== -1
    },
    activeStyle() {
      return this.isActive ? {color: this.activeColor} : {}
    }
  },
}
</script>

<style scoped>
.tab-bar-item{
  flex: 1;
  text-align: center;
  font-size: 14px;
  background: #f6f6f6;
}
.tab-bar-item img{
  width: 24px;
  display: block;
  margin: 0 auto;
  margin-top: 3px;
}
</style>
