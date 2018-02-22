<template>
    <ul>
      <li @click="toggle">
        {{model.name}}
        <span v-if="isFolder && hasName">
          {{isOpen ? '[-]' : '[+]'}}
        </span>
      </li>
      <ul v-if="isFolder" v-show="isOpen || !hasName">
        <item 
          v-for="model in model.children"
          v-bind:model="model"
        >
        </item>
      </ul>
      

    </ul>


      
</template>

<script>
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
    isFolder: function(){
      return this.model.children && this.model.children.length;
    },
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
    }
  }
}
</script>

