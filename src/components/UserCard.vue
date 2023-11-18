<template>
  <div class="user-card">
    <h2>{{ user.name }}</h2>
    <button type="button" @click="btnOnClick">{{ btnContent }}</button>
    <div v-show="showDetails">
      <p>{{ user.email }}</p>
      <p>{{ user.phone }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      btnContent: "显示详情",
      showDetails: false,
    };
  },
  methods: {
    btnOnClick() {
      this.btnContent = this.showDetails ? "显示详情" : "隐藏";
      this.showDetails = !this.showDetails;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.user-card {
  padding: 20px;
  width: 250px;
  cursor: pointer;
  border: 1px solid #39495c;
  margin-bottom: 18px;
}

.user-card:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2);
}
</style>
