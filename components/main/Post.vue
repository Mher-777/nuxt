<template>
  <el-card
    shadow="hover"
    :body-style="{padding: 0}"
    class="post"
  >
    <header slot="header" class="post-header">
      <h3>Post title</h3>

      <small>
        <i class="el-icon-time"></i>
        {{new Date().toLocaleString()}}
      </small>
    </header>
    <div class="post-body">
      <img
        src="https://www.sustaineurope.com/images/berlin%20skyline%20enhanced.jpg?crc=4293215858"
        alt="post image"
        class="post-img">
    </div>
    <footer class="post-footer">
      <el-button round @click="openPost">Открыть</el-button>

      <span>
        <i class="el-icon-message"></i>
        12
      </span>
    </footer>
  </el-card>
</template>

<script>
export default {
  methods: {
    openPost() {
      const id = 'test-id'
      this.$router.push(`/post/${id}`)
    }
  }
}
</script>

<style lang="scss" scoped>
  .post {
    border: 1px solid #EBEEF5;
    margin-bottom: 2rem;
    &-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    &-img {

    }

    &-body {
      img {
        width: 100%;
        max-height: 300px;
        min-height: 250px;
        height: auto;
        display: block;
        object-fit: cover;
      }
    }

    &-footer {
      padding: 10px 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
  }
</style>
