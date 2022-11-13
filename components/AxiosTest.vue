<!-- Please remove this file from your project -->
<template>
  <div>
    <!-- {{ info.data.title }} -->
    <li v-for="(item, index) in info">
      {{ item.Company }}
    </li>
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
