<template>
  <div class="flex flex-col items-center p-10">
    <div class="flex flex-row self-start px-10">
      <button
        v-for="(entry, index) in filterList"
        :item="entry"
        :key="index"
        @click="
          filter = entry;
          active = index;
          resultsFilter();
        "
        :class="{ active: entry == filter }"
      >
        {{ entry }}
      </button>
    </div>
    <div class="grid lg:grid-cols-3 grid-cols-1 gap-8">
      <div
        v-for="(entry, index) in users"
        :key="index"
        data-aos="fade-in"
        data-aos-duration="1000"
      >
        <Card
          :title="entry.Title"
          :description="entry.Description"
          :company="entry.Company"
          :rate="entry.Max_Hourly_Rate"
          :employment="entry.Employment_Type"
          :hours="entry.Hours_Per_Week"
          :seniority="entry.Seniority"
          :location="entry.Location"
          :skills="entry.skills"
          :email="entry.Client_email"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "DataDisplay",
  data: function () {
    return {
      fkey: "mainLanguage",
      filterList: ["Seniority", "Talent Type", "Reset"],
      filter: "Reset",
      users: [],
      info: null,
    };
  },
  methods: {
    resultsFilter() {
      if (this.filter == "Reset") {
        axios
          .get(
            "https://lawtrades-be.herokuapp.com/v1/public/positions?status=Publish"
          )
          .then((response) => {
            this.users = response.data.data;
          });
      }

      if (this.filter == "Talent Type") {
        console.log("Talent Type");
        let newTalent = [];
        console.log(
          "talent type",
          this.users.map((item) => item.Talent_Type)
        );
        let sortedUsers = this.users.sort(function (a, b) {
          var textA = a.Talent_Type.toUpperCase();
          var textB = b.Talent_Type.toUpperCase();
          return textA < textB ? -1 : textA > textB ? 1 : 0;
        });
        console.log("sortedUsers", sortedUsers);
        console.log(
          "sortedUsers list",
          sortedUsers.map((item) => item.Talent_Type)
        );
        this.users = sortedUsers;
      }

      if (this.filter == "Seniority") {
        console.log("Seniority");
        let newSeniority = [];
        console.log(
          "seniority-type",
          this.users.map((item) => item.Seniority)
        );
        this.users.forEach((item) => {
          if (item.Seniority === "senior") {
            console.log("senior detected");
            newSeniority.push(item);
            console.log("newSeniority", newSeniority);
            this.users.forEach((item) => {
              if (item.Seniority === "midLevel") {
                console.log("midLevel detected");
                newSeniority.push(item);
                console.log("newSeniority", newSeniority);
              }
            });
            this.users.forEach((item) => {
              if (item.Seniority === "junior") {
                console.log("junior detected");
                newSeniority.push(item);
                console.log("newSeniority", newSeniority);
              }
            });
          }
        });
        console.log(
          "seniority-type v2",
          newSeniority.map((item) => item.Seniority)
        );
        console.log(this.users);
        this.users = newSeniority;
      }
    },
  },
  mounted() {
    axios
      .get(
        "https://lawtrades-be.herokuapp.com/v1/public/positions?status=Publish"
      )

      .then((response) => {
        this.info = response.data.data;
        this.users = response.data.data;
        console.log("users", this.users);
      });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {
  /* background: #74b6cc;
  border: none;
  color: #fff; */
  padding: 10px;
  margin: 5px;
  @apply inline-block rounded-lg bg-indigo-600 px-4 py-1.5 text-base font-semibold leading-7 text-white shadow-sm ring-1 ring-indigo-600 hover:bg-indigo-700 hover:ring-indigo-700;
}
button.active {
  background: #0089ba;
}
.userWrap {
  list-style-type: none;
  padding: 2%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  flex-direction: row;
}
.user {
  padding: 10px;
  margin: 1% 0;
  border: 1px solid #ddd;
  border-radius: 3px;
  width: 46%;
  text-align: left;
}
h2.title {
  font-size: 1.3rem;
  font-weight: bold;
  margin: 0;
}
.language {
  display: block;
  font-size: 0.9rem;
}
</style>
