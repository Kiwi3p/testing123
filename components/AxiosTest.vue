<!-- Please remove this file from your project -->
<template>
  <div class="grid grid-cols-3 gap-3">
    <!-- {{ info.data.title }} -->
    
    <div class="" v-for="(item, index) in info" data-aos="fade-in" data-aos-duration="1000">
      <Card :title="item.Title" :description="item.Description" :company="item.Company" />
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import axios from "axios";
export default {
  data() {
    return {
      info: null,
    };
  },
  mounted() {
    axios
      .get(
        "https://lawtrades-be.herokuapp.com/v1/public/positions?status=Publish"
      )
      // .get("https://api.coindesk.com/v1/bpi/currentprice.json")
      .then((response) => {
        this.info = response.data.data;
        console.log(this.info);
      });
  },
};
</script>
