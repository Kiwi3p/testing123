<template>
  <div>
  

    <DataDisplay />
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import axios from "axios";

export default Vue.extend({
  name: "IndexPage",
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
});
</script>
