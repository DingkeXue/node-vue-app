<template>
  <div class="profiles">
        <div class="container">
            <div class="row">
                <div class="col-md-12">
                    <h1 class="text-center">致开发者们</h1>
                    <p class="lead text-center mb-5">让世界丰富多彩的你们，让编程改变世界！</p>
                    <!-- 展示开发者 -->
                    <ProfileItem
                      v-if="profiles.length>0"
                      v-for="profileItem in profiles"
                      :key="profileItem._id"
                      :profileItem="profileItem"
                    />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import ProfileItem from './common/ProfileItem';
export default {
  name: 'profiles',
  data() {
    return {
      profiles: []
    };
  },
  created() {
    this.getProfiles();
  },
  components: {
    ProfileItem
  },
  methods: {
    getProfiles() {
      this.$axios
        .get('/api/profile/all')
        .then(res => {
          // console.log(res.data);
          this.profiles = res.data;
          this.$store.dispatch('setProfiles', res.data);
        })
        .catch(err => {
          this.profiles = [];
          this.$store.dispatch('setProfiles', []);
        });
    }
  }
};
</script>

<style scoped>
  .profiles {
    margin: 30px 0 30px 0;
  }
</style>

