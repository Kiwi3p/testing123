<template>
  <div
    data-aos="fade-up"
    data-aos-duration="1000"
    class="max-w-md py-4 px-8 bg-white shadow-lg rounded-lg my-20"
  >
    <!-- <div class="flex justify-center md:justify-end -mt-16">
      <img
        class="w-20 h-20 object-cover rounded-full border-2 border-indigo-500"
        src="https://images.unsplash.com/photo-1499714608240-22fc6ad53fb2?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=334&q=80"
      />
    </div> -->
    <div class="flex justify-end mt-4">
      <a href="#" class="text-xl font-medium text-indigo-500">{{ company }}</a>
    </div>
    <div>
      <h2 class="text-gray-800 text-3xl font-semibold">{{ title }}</h2>
      <p class="mt-2 text-gray-600">
        <span v-if="open == true">
          {{ description }}
          <div>
            <h1>rate: $0000</h1>
            <h2>Employment type: part time</h2>
            <h3>Hours Per Week: 35</h3>
            <h3>Duration</h3>
            <h4>Location</h4>
            <h5>Hourly Rate</h5>
            <h6>Skills:</h6>
            <ul>
              <li>test</li>
              <li>test</li>
              <li>test</li>
            </ul>
          </div>
        </span>
        <span v-else>
          {{ subString }}
        </span>
      </p>
    </div>

    <!-- <button v-if="open" @click="open = false">Close</button>
    <button v-else @click="open = true">See Description</button> -->

    <div class="flex justify-end mt-4">
      <!-- <a href="#" class="text-xl font-medium text-indigo-500">See more</a> -->
      <button
        class="text-xl font-medium text-indigo-500"
        v-if="open"
        @click="open = false"
      >
        Close
      </button>
      <button
        class="text-xl font-medium text-indigo-500"
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
  props: ["title", "description", "company"],
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
