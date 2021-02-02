<template>
  <article class="post">
    <header class="post-header">
      <div class="post-title">
        <h1>Post title id:({{$route.params.id}})</h1>
        <nuxt-link to="/">
          <i class="el-icon-back"></i>

        </nuxt-link>
      </div>
      <div class="post-info">
        <small>
          <i class="el-icon-time"></i>
          {{new Date().toLocaleString()}}
        </small>
        <small>
          <i class="el-icon-view"></i>
          42
        </small>
      </div>
      <div class="post-image">
        <img
          src="https://www.sustaineurope.com/images/berlin%20skyline%20enhanced.jpg?crc=4293215858"
          alt="post-main">
      </div>
    </header>
    <main class="post-content">
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aut libero, odio omnis perferendis provident quae quasi quia suscipit vel vero!</p>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aut libero, odio omnis perferendis provident quae quasi quia suscipit vel vero!</p>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aut libero, odio omnis perferendis provident quae quasi quia suscipit vel vero!</p>
    </main>
    <footer>
      <app-comment-form
        v-if="canAddComment"
        @created="createCommentHandler"
      />
      <div class="comment" v-if="true">
        <app-comment
          v-for="comment in 4" :key="comment" :comment="comment"
        />
      </div>
      <div class="text-center" v-else>Комментариев нет</div>
    </footer>
  </article>
</template>

<script>
import AppComment from '@/components/main/Comment'
import AppCommentForm from '@/components/main/CommentForm'
export default {
  validate({params}) {
    return Boolean(params.id)
  },
  components: {
    AppComment,
    AppCommentForm
  },
  data () {
    return {
      canAddComment: true
    }
  },
  methods: {
    createCommentHandler() {
      this.canAddComment = false
    }
  }
}
</script>

<style lang="scss" scoped>
  .post {
    max-width: 600px;
    margin: 0 auto;
    border: 1px solid #EBEEF5;
    padding: .5rem;
    &-header {

    }
    &-title {
      display: flex;
      justify-content: space-between;
      margin-bottom: 1rem;
      align-items: center;
    }
    &-info {
      display: flex;
      justify-content: space-between;
      margin-bottom: .5rem;
      align-items: center;
    }
    &-image {
      margin: 0 -.5rem;
      img {
        max-width: 100%;
        width: 100%;
        height: auto;
        display: block;
        object-fit: cover;
      }
    }
    &-content {
      padding: 1rem 0;
    }
  }
</style>
