<template>
  <div class="posts">
        <!-- Post Item -->
        <div class="card card-body mb-3">
          <div class="row">
            <div class="col-md-2 mr-5">
              <a v-if="post.avatar" href="profile.html">
                <img class="rounded-circle img" :src="post.avatar"
                  alt="头像" />
              </a>
              <p class="text-center mt-2">{{post.name}}</p>
            </div>
            <div class="col-md-9">
              <p class="lead mt-3">{{post.text}}</p>
              <span v-if="showAction">
              <button @click="likeClick(post._id)" type="button" class="btn btn-light mr-1">
                <i class="text-info fas fa-thumbs-up"></i>
                <span class="badge badge-light">{{post.likes.length}}</span>
              </button>
              <button @click="unlikeClick(post._id)" type="button" class="btn btn-light mr-1">
                <i class="text-secondary fas fa-thumbs-down"></i>
              </button>
              <router-link :to="'/post/'+post._id" class="btn btn-info mr-1">给Ta留言</router-link>
              <button @click="deleteClick(post._id)" v-if="user != null && user.id == post.user" type="button" class="btn btn-danger mr-1">
                <i class="fas fa-trash-alt" />
              </button>
                <p v-if="liked" class="showErr">
                  {{liked.alreadyliked}}
                </p>
                <p v-if="unLike" class="showErr">
                  {{unLike.notliked}}
                </p>
              </span>
            </div>
          </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'postFeed',
  data() {
    return {
      liked: null,
      unLike: null
    };
  },
  computed: {
    user() {
      return this.$store.getters.user;
    }
  },
  props: {
    post: Object,
    showAction: Boolean
  },
  methods: {
    deleteClick(id) {
      this.$axios
        .delete(`/api/posts/${id}`)
        .then(res => {
          // 删除成功 更新数据
          this.$emit('update');
        })
        .catch(err => {
          console.log(err.response.data);
        });
    },
    likeClick(id) {
      this.$axios
        .post(`/api/posts/like/${id}`)
        .then(res => {
          // 成功 更新数据
          this.liked = null;
          this.unLike = null;
          this.$emit('update');
        })
        .catch(err => {
          this.linked = err.response.data;
        });
    },
    unlikeClick(id) {
      this.$axios
        .post(`/api/posts/unlike/${id}`)
        .then(res => {
          // 成功 更新数据
          this.liked = null;
          this.unLike = null;
          this.$emit('update');
        })
        .catch(err => {
          this.unLike = err.response.data;
        });
    }
  }
};
</script>

<style scoped>
  .img {
    width: 100%;
  }
  .showErr {
    color: red;
  }
</style>

