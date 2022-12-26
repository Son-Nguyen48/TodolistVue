<template>
  <div class='todo'>
    <h1
      :class="{
        'title-default': items.length===0,
        'title-red': count===0&&items.length!==0||count<items.length/2,
        'title-yellow': count>=items.length/2&&count!==0,
        'title-green': items.length===count&&items.length!==0}">
      {{ msg }}</h1>
    <input type='text' v-model='currentValue' class='input-current' />
    <button @click='addItem' class='btn-add'>ADD</button>
    <ul class='ul-list'>
      <li v-for='(item, index) in items' :key='item.id' class='li-item'>
        <button @click='removeItem(index, item)'
          :class="{
            'btn-remove': item,
            'li-cross': item.done===true}">
          {{item.title}}
        </button>
        <input type='checkbox' @click='crossItem(item)' v-model='item.done' />
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'ToDo',
    props: {
      msg: String
    },
    data () {
      return {
        items:[],
        currentValue:'',
        count:0
      }
    },
    methods: {
      addItem() {
        this.currentValue?this.items.push({
          title: this.currentValue,
          done: false
        }):false;
        this.currentValue='';
      },
      crossItem(item) {
        item.done = !item.done;
        item.done?this.count++:this.count--;
      },
      removeItem(index, item) {
        this.items.splice(index, 1);
        (this.count!==0&&item.done)?this.count--:false;
      }
    }
  }
</script>

<style scoped lang='scss'>
  @mixin btn-style {
    font-weight: 700;
    color: white;
    background-color: rgb(70, 42, 82);
    border: 1px solid rgb(17, 1, 34);
    border-radius: 2px;
  }
  .ul-list {
    list-style-type: none;
    padding: 0;
  }
  .li-cross {
    text-decoration: line-through;
  }
  .title-default {
    color:rgb(17, 1, 34);
  }
  .title-red {
    color: red;
  }
  .title-yellow {
    color: yellow;
  }
  .title-green {
    color: green;
  }
  input[type=text] {
    width: 300px;
    height: 30px;
    border: 1px solid rgb(17, 1, 34);
    border-radius: 2px;
  }
  .btn-add {
    height: 34px;
    width: 45px;
    @include btn-style;
  }
  .btn-remove {
    width: 250px;
    height: 30px;
    @include btn-style;
  }
  input[type=checkbox] {
    height: 31px;
    width: 45px;
    margin: 0;
  }
  .li-item {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items:center;
    margin-bottom: 5px;
  }
</style>
