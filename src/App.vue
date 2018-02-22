<template>
  <ul id="app">
    <item
      :model="treeData"
    >
    </item>
  </ul>
</template>

<script>
import item from './item.vue';
var data = {
name: 'my tree',
children: [
        { name: 'hello' },
        { name: 'wat' },
        {
        name: 'child folder',
        children: [
            {
            name: 'child folder',
            children: [
                { name: 'hello' },
                { name: 'wat' }
            ]
            },
            { name: 'hello' },
            { name: 'wat' },
            {
            name: 'child folder',
            children: [
                { name: 'hello' },
                { name: 'wat' }
            ]
            }
        ]
        }
    ]
}
export default {
  name: 'app',
  components :{
    item
  },
  data () {
    return {
      name: 'my tree',
      treeData: data
    }
  }
}
</script>
