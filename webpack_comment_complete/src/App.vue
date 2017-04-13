<template>
  <header class="site-header jumbotron">
    <div class="container">
      <div class="row">
        <div class="col-xs-12">
          <h1>请发表对Vue的评论</h1>
        </div>
      </div>
    </div>
  </header>
  <div class="container">
    <div class="col-md-4">
      <form class="form-horizontal">
        <div class="form-group">
          <label>用户名</label>
          <input type="text" class="form-control" placeholder="用户名" v-model='comment.name'>
        </div>
        <div class="form-group">
          <label>评论内容</label>
          <textarea class="form-control" rows="6" placeholder="评论内容" v-model='comment.content'></textarea>
        </div>
        <div class="form-group">
          <div class="col-sm-offset-2 col-sm-10">
            <button type="button" class="btn btn-default pull-right" @click='submited()'>提交</button>
          </div>
        </div>
      </form>
    </div>
    <div class="col-md-8">
      <h3 class="reply">评论回复：</h3>
      <h2 style='display: none'>暂无评论，点击左侧添加评论！！！</h2>
      <ul class="list-group">
        <li class="list-group-item" v-for='comment in comments'>
          <div class="handle">
            <a href="javascript:;" @click='deleteComment($index, comment)'>删除</a>
            <a href="javascript:;" @click='deleteComment2(comment)'>删除2</a>
          </div>
          <p class="user"><span >{{comment.name}}</span><span>说:</span></p>
          <p class="centence">{{comment.content}}</p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        comments: [],
        comment: {}
      }
    },
    created () {
      setTimeout(() => {
        this.comments = [
          {id: 1, name: 'lala', content: 'Vue还不错是吧'},
          {id: 2, name: 'kaka', content: '恩恩是的'}
        ]
      })
    },
    methods: {
      submited () {
        this.comment.id = Date.now()
        this.comments.unshift(this.comment)
        this.comment = {}
      },
      deleteComment (index, comment) {
        if (window.confirm(`你确定删除${comment.name}的评论么?`)) {
          this.comments.splice(index, 1)
        }
      },
      deleteComment2 (comment) {
        if (window.confirm(`你确定要删除${comment.name}的评论么?`)) {
          this.comments.$remove(comment)
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
