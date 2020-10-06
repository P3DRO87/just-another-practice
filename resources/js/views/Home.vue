<template>
  <div class="container-fluid main">
    <div class="mt-4">
      <scale-loader :loading="isLoading" :color="`#6c757d`" :size="200"></scale-loader>
    </div>
    <MainTable v-if="!isLoading" class="table" :assets="assets" />
  </div>
</template>

<script>
import api from "../api";
import MainTable from "../components/MainTable";

export default {
  name: "Home",

  components: {
    MainTable
  },

  data() {
    return {
      isLoading: true,
      assets: []
    };
  },

  created() {
    api
      .getAssets()
      .then(assets => (this.assets = assets))
      .finally(() => {
        this.isLoading = false;
      });
  }
};
</script>
