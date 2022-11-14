<template>
  <div>
    Positions test
    <DataDisplay />
    <!-- <Recipes /> -->
    <AxiosTest />
    <!-- <AccordionV2 /> -->
    <!-- <div

      class="container mx-auto bg-white border-grey-light border mt-20"
    >
      <accordion title="Trevor Belmont">
        <p class="pb-5">
          Lorem ipsum dolor sit amet, ut alii voluptaria est, ad illum inimicus
          deterruisset eam. His eu bonorum adipisci definiebas, no vis nostrud
          conclusionemque. Ad his virtute accusata, pro habemus singulis
          temporibus ut, ne bonorum dolores euripidis quo. No nam amet erant
          intellegebat. Rationibus instructior id pri, vis case abhorreant ea,
          id sea meis feugiat.
        </p>

        <p class="pb-5">
          Ut vel percipit facilisi, sea partem veritus mandamus eu, at debet
          deleniti eos. Iudico suscipit mel ut. Per ad habeo sadipscing
          concludaturque. Pri lorem fastidii in, accusam honestatis
          signiferumque est ut, ea eos omnium senserit reprehendunt. Eu est nibh
          invenire.
        </p>
      </accordion>

    
    </div> -->
    <!-- <Tutorial/> -->
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
