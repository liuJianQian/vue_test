<template>
  <div class="col-md-8">
    <h3 class="reply">评论回复：</h3>
    <h2 v-show='comments.length===0'>暂无评论，点击左侧添加评论！！！</h2>
    <ul class="list-group" v-show='comments.length'>
      <comment-item v-for="comment in comments" :comment='comment' :index='$index' :remove='remove'></comment-item>
    </ul>
  </div>
</template>

<script>
  import CommentItem from './CommentItem'
  export default {
    // props: ['comments'],
    props: {
      comments: {
        type: Array
      },
      remove: Function
    },
    components: {
      CommentItem
    }
  }
</script>

<style scoped>
  .reply {
    margin-top: 0px;
  }

  li {
    transition: .5s;
    overflow: hidden;
  }

  .list-group-item .centence {
    padding: 0px 50px;
  }

  .user {
    font-size: 22px;
  }
</style>
