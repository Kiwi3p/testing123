<template>
  <div class="flex justify-center px-4">
    <div class="max-w-4xl bg-white w-full rounded-lg shadow-xl">
      <div>
        <div
          class="md:grid md:grid-cols-2 hover:bg-gray-50 md:space-y-0 space-y-1 p-4 border-b"
        >
          <p class="text-gray-600 font-bold">Employment type:</p>
          <p>{{ employment }}</p>
        </div>
        <div
          class="md:grid md:grid-cols-2 hover:bg-gray-50 md:space-y-0 space-y-1 p-4 border-b"
        >
          <p class="text-gray-600 font-bold">Rate:</p>
          <p>${{ rate }}</p>
        </div>
        <div
          class="md:grid md:grid-cols-2 hover:bg-gray-50 md:space-y-0 space-y-1 p-4 border-b"
        >
          <p class="text-gray-600 font-bold">Hours Per Week:</p>
          <p>{{ hours }}</p>
        </div>
        <div
          class="md:grid md:grid-cols-2 hover:bg-gray-50 md:space-y-0 space-y-1 p-4 border-b"
        >
          <p class="text-gray-600 font-bold">Seniority:</p>
          <p>{{ seniority }}</p>
        </div>
        <div
          class="md:grid md:grid-cols-1 hover:bg-gray-50 md:space-y-0 space-y-1 p-4 border-b"
        >
          <p class="text-gray-600 font-bold">Description</p>
          <p>
            {{ description }}
          </p>
        </div>
        <div
          class="md:grid md:grid-cols-2 hover:bg-gray-50 md:space-y-0 space-y-1 p-4 border-b"
        >
          <p class="text-gray-600">Skills:</p>
          <ul>
            <li v-for="(item, index) in skills">{{ item.skill.name }}</li>
          </ul>
        </div>
        <div
          class="md:grid md:grid-cols-2 hover:bg-gray-50 md:space-y-0 space-y-1 p-4 border-b"
        >
          <p class="text-gray-600"></p>
          <a
            :href="`mailto:${email}`"
            class="inline-block rounded-lg bg-indigo-600 px-4 py-1.5 text-base font-semibold leading-7 text-white shadow-sm ring-1 ring-indigo-600 hover:bg-indigo-700 hover:ring-indigo-700"
          >
            Contact Now
          </a>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "card",
  props: [
    "title",
    "description",
    "company",
    "rate",
    "employment",
    "hours",
    "seniority",
    "location",
    "skills",
    "email",
  ],
  data() {
    return {};
  },
  metaInfo() {
    return {
      title: this.title,
      meta: [
        { vmid: "description", name: "description", content: this.description },
      ],
    };
  },
};
</script>
