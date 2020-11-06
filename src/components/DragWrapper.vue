<template>
  <div ref="dragEle" draggable="true" class="wrap">
    <slot/>
  </div>
</template>

<script>
export default {
  name: 'DragWrapper',
  props: {
    itemIndex: Number,
  },
  mounted: function() {
    this.$refs['dragEle'].addEventListener('dragstart', this.dragStart)
    this.$refs['dragEle'].addEventListener('dragover', this.dragOver)
    this.$refs['dragEle'].addEventListener('drop', this.finalDrop)
  },
  beforeDestroy: function() { 
    this.$refs['dragEle'].removeEventListener('dragstart', this.dragStart)
    this.$refs['dragEle'].removeEventListener('dragover', this.dragOver)
    this.$refs['dragEle'].removeEventListener('drop', this.finalDrop)
  },
  methods: {
    dragStart(e) {
      console.log('startdrag')
      e.dataTransfer.setData('dragIndex', this.itemIndex)
    },
    dragOver(e) {
      e.preventDefault()
    },
    finalDrop(e) {
      this.$emit('sort-by-drag', {
        preIndex: e.dataTransfer.getData('dragIndex'),
        nextIndex: this.itemIndex,
      })
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
