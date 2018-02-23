<template>
    <li >
      <div @click="toggle" :class="{bold: isFolder}" @dblclick="changeType">
        {{model.name}}
        <!-- 這邊為上層 -->
        <!-- 判斷若有下層, 就會出現開合符號 -->
        <span v-if="isFolder && hasName">
          {{isOpen ? '[-]' : '[+]'}}
        </span>
      </div>
      
      <!-- 若目前為開啟狀態或沒 -->
      <ul v-show="isOpen && isFolder">
        <item 
          v-for="model in model.children"
          :key="model.name"
          :model="model"
        >
        </item>
        <li @click="addList">+</li>
      </ul>
    </li>

    



      
</template>

<script>
import Vue from 'vue'

export default {
  name: 'item',
  props: {
    model:{
        type: Object, //型態
        default: function(){ //預設
            return [];
        }
    }
  },
  computed:{
    //判斷是否有下層結構
    isFolder: function(){
      return this.model.children && this.model.children.length;
    },
    //判斷父層有無名稱
    hasName: function(){
      return this.model.name !== undefined;
    }
  },
  data () {
    return {
      isOpen: true,
    
    }
    
  },
  methods: {
    toggle: function(){
      if(this.isFolder){
        this.isOpen = !this.isOpen;
      }
    },
    changeType: function(){
      if(!this.isFolder){ //若不是檔案目錄則轉換為目錄
        Vue.set(this.model,"children",[]);
        this.addList();//加入新的 name;
        this.isOpen = true;
      }
    },
    addList: function(){
      console.log(this.model.children.push({"name": "new item"}) );
    }
  }
}
</script>

<style lang="scss">
  #app{

    li{
      cursor: pointer;
    }
    .bold{
      font-weight: bold;
    }
    div{
      display:inline-block;
    }
  }

</style>
