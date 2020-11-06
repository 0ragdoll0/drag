<template>
  <div id="app">
    <h3>Drag Project</h3>
    <DragWrapper v-for="(item, index) in list" :key="item.id" :item-index="index" @sort-by-drag="onDragItem">
      <div class="drag-item">{{index+1}}.{{item.text}}</div>
    </DragWrapper>
  </div>
</template>

<script>
import DragWrapper from './components/DragWrapper.vue'

export default {
  name: 'App',
  components: {
    DragWrapper
  },
  data: function() {
    return {
      list: [{id:101,text:'西游记'},{id:102,text:'红楼梦'},{id:103,text:'水浒传'},{id:104,text:'三国演义'}],
    }
    
  },
  methods: {
    onDragItem(indexInfo) {
      const dragItem = this.list.splice(
        indexInfo.preIndex,
        1,
      )[0]
      this.list.splice(indexInfo.nextIndex, 0, dragItem)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  text-align: center;
}
.drag-item {
  width: 200px;
  height: 80px;
  line-height: 80px;
  margin: 20px auto;
  border: 1px dotted gray;
  border-radius: 3px;
}
</style>
