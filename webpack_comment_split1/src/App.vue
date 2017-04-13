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
      <add-comment :add-comment='addComment'></add-comment>
      <list-comment :comments='comments' :delete-comment='deleteComment' :deleteComment='deleteComment'></list-comment>
    </div>
</template>

<script>
  import AddComment from 'components/AddComment.vue'
  import ListComment from 'components/ListComment.vue'
  export default {
    data () {
      return {
        comments: []
      }
    },
    created () {
      setTimeout(() => {
        this.comments = [
          {id: 1, name: 'lala', content: 'vue还不错吧'},
          {id: 2, name: 'tata', content: '恩恩,还不错的'}
        ]
      }, 1000)
    },
    methods: {
      addComment (comment) {
        this.comments.unshift(comment)
      },
      deleteComment (index) {
        this.comments.splice(index, 1)
      }
    },
    components: {
      AddComment,
      ListComment
    }
  }
</script>

<style>

</style>
