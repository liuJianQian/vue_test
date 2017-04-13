<template>
    <div>
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
      <comment-add :submited='submited'></comment-add>
      <comment-list :comments="comments" :remove='remove'></comment-list>
    </div>
  </div>
</template>

<script>
  import CommentAdd from 'components/CommentAdd'
  import CommentList from 'components/CommentList'
  export default {
    data () {
      return {
        comments: []
      }
    },
    created () {
      setTimeout(() => {
        this.comments = [
          {id: 1, username: 'sansan', content: 'Vue应该好用!'},
          {id: 2, username: 'xiamu', content: 'Vue试试才知道嘛!'}
        ]
      }, 1000)
    },
    methods: {
      submited (comment) {
        this.comments.unshift(comment)
      },
      remove (index) {
        this.comments.splice(index, 1)
      }
    },
    events: {
      'comment.delete' (index) {
        this.comments.splice(index, 1)
      }
    },
    components: {
      CommentAdd,
      CommentList
    }
  }
</script>

<style>
</style>
