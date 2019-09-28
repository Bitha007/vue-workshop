<template>
  <div class="container">
    <div class="card">
      <div class="comment">
        <div class="comment__img">
          <img src="../assets/ts.jpg" alt="Profile picture" />
        </div>
        <div class="comment__content">
          <ul class="comment-list">
            <li>
              <span></span>
            </li>
          </ul>
          <div class="no-comments">
            <p v-if="!comments.length">No comments added yet</p>
            <div v-for="comment in comments" :key="comment" >
                <div>{{comment}}</div>
            </div> 
          </div>
        </div>
        <div class="comment-box">
          <textarea  @keypress.enter="addComment" class="form-control" v-model="currentComment" rows="3" placeholder="Write a comment"></textarea>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PhotoComment",
  data(){
    return{
      currentComment:"",
      comments:[]
    }
  },
  methods: {
    addComment: function() {
      this.comments = [...this.comments, this.currentComment];
      this.currentComment =""
    }
  },
};
</script>

<style scoped lang="scss">
.container {
  margin: 0 auto;
  max-width: 768px;
}

.card {
  box-shadow: 0 2px 3px rgba(10, 10, 10, 0.1), 0 0 0 1px rgba(10, 10, 10, 0.1);
}

.comment {
  &__img {
    > img {
      width: 100%;
    }
  }
  &__content {
    padding: 18px;

    .comment-list {
      > li {
        &:not(:last-child) {
          margin-bottom: 12px;
        }
        > span {
          background-color: #f2f3f5;
          border-radius: 68px;
          padding: 8px 12px;
          font-size: 14px;
          display: inline-block;
        }
      }
    }
  }
  .comment-box {
    textarea {
      border: 1px solid #f2f2f2;
      width: 100%;
      padding: 12px;
    }
  }
}
</style>
