<template>
  <div class="col-md-8">
    <h3 class="reply">评论回复：</h3>
    <h2 v-show='comments.length===0'>暂无评论，点击左侧添加评论！！！</h2>
    <ul class="list-group" v-show='comments.length'>
     <li class="list-group-item" v-for='comment in comments'>
        <div class="handle">
          <a href="javascript:;" @click='removeItem(comment ,$index)'>删除</a>
        </div>
        <p class="user"><span >{{comment.name}}</span><span>说:</span></p>
        <p class="centence">{{comment.content}}</p>
     </li>
    </ul>
  </div>
</template>

<script>
  export default {
    props: ['comments', 'deleteComment'],
    data () {
      return {

      }
    },
    methods: {
      removeItem (comment, index) {
        let name = comment.name
        if (window.confirm(`确定要删除${name}的评论么?`)) {
          this.deleteComment(this.index)
        }
      }
    }
  }
</script>

<style>
  .reply {
    margin-top: 0px;
  }
    li {
    transition: .5s;
    overflow: hidden;
  }

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

  .list-group-item .centence {
    padding: 0px 50px;
  }

  .user {
    font-size: 22px;
  }
</style>
