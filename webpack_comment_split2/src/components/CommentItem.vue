<template>
  <li class="list-group-item">
    <div class="handle">
      <a href="javascript:;" @click="deleteItem">删除</a>
      <a href="javascript:;" @click="deleteItem2">删除2</a>
    </div>
    <p class="user"><span >{{comment.username}}</span><span>说:</span></p>
    <p class="centence">{{comment.content}}</p>
  </li>
</template>

<script>
  export default {
    props: ['comment', 'index', 'remove'],
    methods: {
      deleteItem () {
        let username = this.comment.username
        if (window.confirm(`确定要删除${username}的评论么?`)) {
          this.remove(this.index)
        }
      },
      deleteItem2 () {
        let username = this.comment.username
        if (window.confirm(`确定删除${username}的评论么?`)) {
          this.$dispatch('comment.delete', this.index)
        }
      }
    }
  }
</script>

<style scoped>
  .handle {
    width: 40px;
    border: 1px solid #ccc;
    background: #fff;
    position: absolute;
    right: 10px;
    top: 1px;
    text-align: center;
  }

  .handle a {
    display: block;
    text-decoration: none;
  }
</style>
