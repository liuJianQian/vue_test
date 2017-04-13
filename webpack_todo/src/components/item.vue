<template>
  <li :style="{background: bgColor}" @mouseenter='toggleColor(true)' @mouseleave='toggleColor(false)'>
    <label>
      <input type="checkbox"/>
      <span>{{todo.text}}</span>
    </label>
    <button class="btn btn-danger" v-show='isShow' @click='removeTodo'>删除</button>
  </li>
</template>

<script>
  export default {
    data () {
      return {
        bgColor: 'white',
        isShow: false
      }
    },
    props: ['todo'],
    methods: {
      removeTodo () {
        if (window.confirm(`你确定删除${this.todo.text}这项么?`)) {
          this.$dispatch('todo_delete', this.todo)
        }
      },
      toggleColor (isEnter) {
        if (isEnter) {
          this.bgColor = '#eee'
          this.isShow = true
        } else {
          this.bgColor = 'white'
          this.isShow = false
        }
      }
    }

  }
</script>

<style>
  /* item */
  li {
    list-style: none;
    height: 36px;
    line-height: 36px;
    padding: 0 5px;
    border-bottom: 1px solid #ddd;
  }

  li label {
    float: left;
    cursor: pointer;
  }

  li label li input {
    vertical-align: middle;
    margin-right: 6px;
    position: relative;
    top: -1px;
  }

  li button {
    float: right;
    display: none;
    margin-top: 3px;
  }

  li:before {
    content: initial;
  }

  li:last-child {
    border-bottom: none;
  }
</style>
