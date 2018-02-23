<template>
  <div id="app">
    點擊兩下可將選單轉為目錄型態
    <item
      :model="treeData"
    >
    </item>
  </div>
</template>

<script>
import item from './item.vue';
var data = {
name: 'my tree',
children: [
        { name: 'dica' },
        { name: 'omg' },
        {
        name: '子目錄',
        children: [
            {
            name: '子目錄',
            children: [
                { name: 'dica' },
                { name: 'nono' }
            ]
            },
            { name: 'dica' },
            { name: 'nono' },
            {
            name: '子目錄',
            children: [
                { name: 'dica' },
                { name: 'nono' }
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
