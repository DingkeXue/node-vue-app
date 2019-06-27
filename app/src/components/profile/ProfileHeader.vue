<template>
  <div class="row">
    <div class="col-md-12">
      <div class="card card-body bg-info text-white mb-3">
        <div class="row">
          <div class="col-md-12 text-center">
            <img v-if="profile.user" class="rounded-circle" :src="profile.user.avatar" alt="头像" />
            <h1 v-if="profile.user" class="display-4 text-center">{{profile.user.name}}</h1>
            <p v-if='profile.company' class="lead text-center">{{profile.company}}</p>
            <p v-if="profile.location">{{profile.location}}</p>
            <p>
              <a v-if="profile.social && profile.social.wechat" class="text-white p-2" >
                <i class="fab fa-weixin fa-2x"></i>
              </a>
              <a v-if='profile.social && profile.social.QQ' class="text-white p-2">
                <i class="fab fa-qq fa-2x"></i>
              </a>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'profileHeader',
  data() {
    return {};
  },
  props: {
    profile: Object
  }
};
</script>

<style scoped>
</style>

