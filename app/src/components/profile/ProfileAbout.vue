<template>
  <div class="row">
    <div class="col-md-12">
      <div class="card card-body bg-light mb-3 text-center">
        <h3 class="text-info">个人介绍</h3>
        <p class="lead">
            <span v-if="profile.bio">{{profile.bio}}</span>
            <span v-else>没有填写介绍信息</span>
        </p>
        <hr />
        <h3 class="text-info">个人技能</h3>
        <div class="row">
            <div class="p-3" v-for="(skill, index) in profile.skills" :key="index">
              <i class="fa fa-check"></i> {{skill}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'profileAbout',
  data() {
    return {};
  },
  props: {
    profile: Object
  }
};
</script>

<style scoped>
  .row {
    justify-content: center;
  }
</style>

