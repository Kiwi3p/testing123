<template>
  <div
    data-aos="fade-up"
    data-aos-duration="1000"
    class="max-w-md py-4 px-8 bg-white shadow-lg rounded-lg my-20"
  >
  
    <div class="flex justify-end mt-4">
      <span class="text-xl font-medium text-indigo-500">{{ company }}</span>
    </div>
    <div>
      <h2 class="text-gray-800 text-3xl font-semibold">{{ title }}</h2>
      <div class="mt-2 text-gray-600">
        <div v-if="open == true">
          
          <Profile :rate="rate" :description="description" :employment="employment" :hours="hours" :seniority="seniority" :location="location" :email="email" :skills="skills"/>
        </div>
        <span v-else>
          {{ subString }}
        </span>
    </div>
    </div>



    <div class="flex justify-end mt-4">

      <button
        class="inline-block rounded-lg bg-indigo-600 px-4 py-1.5 text-base font-semibold leading-7 text-white shadow-sm ring-1 ring-indigo-600 hover:bg-indigo-700 hover:ring-indigo-700"
        v-if="open"
        @click="open = false"
      >
        Close
      </button>
      <button
        class="inline-block rounded-lg bg-indigo-600 px-4 py-1.5 text-base font-semibold leading-7 text-white shadow-sm ring-1 ring-indigo-600 hover:bg-indigo-700 hover:ring-indigo-700"
        v-else
        @click="open = true"
      >
        See More
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "card",
  props: ["title", "description", "company", 'rate', 'employment', 'hours', 'seniority', 'location', 'skills', 'email'],
  data() {
    return {
      open: false,
      subString: "",
    };
  },
  metaInfo() {
    return {
      title: this.title,
      meta: [
        { vmid: "description", name: "description", content: this.description },
      ],
    };
  },
  mounted() {
    this.subString = `${this.description.substring(0, 50)}...`;
  },
};
</script>
