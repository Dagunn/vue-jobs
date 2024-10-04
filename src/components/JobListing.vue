<script setup>
import { defineProps, ref, computed } from 'vue';
import { RouterLink } from 'vue-router';

const props = defineProps({
  bg: {
    type: String,
    default: 'bg-neutral-800',
  },

  job: {
    type: Object,
  },
});

const showFullDescription = ref(false);

const toggleDescription = () => {
  showFullDescription.value = !showFullDescription.value;
};

const shortDescription = computed(() => {
  let description = props.job.description;

  if (!showFullDescription.value) {
    description = description.substring(0, 90) + '...';
  }
  return description;
});
</script>

<template>
  <div
    :class="`${bg} rounded-xl text-white border-green-500 border shadow-md relative card-box`"
  >
    <div class="p-4">
      <div class="mb-6">
        <div class="text-green-500 my-2">{{ job.type }}</div>
        <h3 class="text-xl font-bold">{{ job.title }}</h3>
      </div>

      <div class="mb-5">
        <div>
          {{ shortDescription }}
        </div>
        <button
          class="text-green-500 :hover:text-green-600 mb-5"
          @click="toggleDescription"
        >
          {{ showFullDescription ? 'Less' : 'More' }}
        </button>
      </div>

      <h3 class="text-green-500 mb-2">{{ job.salary }} / Year</h3>

      <div class="border border-gray-100 mb-5"></div>

      <div class="flex flex-col lg:flex-row justify-between mb-4">
        <div class="text-orange-700 mb-3">
          <i class="pi pi-map-marker text-lg text-orange-700"></i>
          {{ job.location }}
        </div>
        <RouterLink
          :to="'/jobs/' + job.id"
          class="h-[36px] bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg text-center text-sm"
        >
          Read More
        </RouterLink>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card-box {
  filter: drop-shadow(1px 1px 5px rgb(34 197 94));
  border-radius: 16px;
}

.hide {
  display: none;
}
</style>
