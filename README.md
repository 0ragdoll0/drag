# drag-pro

## 拖拽实现数据顺序的改变

### 使用 src/components/DragWrapper 组件

可参考`App.vue`中`DragWrapper`的使用

- 实际展示的内容通过`slot`传入`DragWrapper`
- 需要设置`@sort-by-drag="onDragItem"`，改变数据的顺序

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).
