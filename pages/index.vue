<template>
  <div class="relative h-screen">
    <div
      class="fixed z-0 w-full h-full bg-cover bg-gradient-to-r from-purple-100 to-purple-200"
    ></div>
    <div class="container mx-auto py-12">
      <div class="grid grid-cols-12 z-10">
        <div class="col-span-12 flex justify-center mb-8 z-10">
          <span class="text-2xl font-extrabold text-gray-700">
            Our Pricing
          </span>
        </div>
        <div class="col-span-12 flex justify-center mb-24 z-10">
          <div class="grid grid-cols-3 gap-8 items-center">
            <div class="flex justify-center">
              <span class="font-semibold text-gray-500">Annually</span>
            </div>
            <div class="flex justify-center">
              <div @click="toggleTime()">
                <toggle :isActive="isMonthly" />
              </div>
            </div>
            <div class="flex justify-center">
              <span class="font-semibold text-gray-500">Monthly</span>
            </div>
          </div>
        </div>
        <div class="col-span-12 flex justify-center">
          <div class="grid grid-cols-3 gap-4">
            <div
              v-for="item in dataPricing"
              :key="item.id"
              class="flex relative z-10"
              :class="{ 'z-20': item.isCenter }"
            >
              <card :data="item" :isMonthly="isMonthly" />
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="absolute bottom-0 left-0">
      <div class="fixed bottom-0">
        <img src="~/assets/image/bg-bottom.svg" alt="" />
      </div>
    </div>
    <div class="absolute top-0 right-0">
      <div class="fixed right-0">
        <img src="~/assets/image/bg-top.svg" alt="" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import Card from "~/components/Card.vue";
import Toggle from "~/components/Toggle.vue";

export default Vue.extend({
  components: { Toggle, Card },
  data() {
    return {
      isMonthly: false,
      dataPricing: [
        {
          id: 1,
          name: "Basic",
          priceAnnually: 199.99,
          priceMonthly: 19.99,
          feature: ["500 GB Storage", "2 Users Allowed", "Send up to 3 GB"],
          isCenter: false,
        },
        {
          id: 2,
          name: "Professional",
          priceAnnually: 249.99,
          priceMonthly: 24.99,
          feature: ["1 TB Storage", "5 Users Allowed", "Send up to 10 GB"],
          isCenter: true,
        },
        {
          id: 3,
          name: "Master",
          priceAnnually: 399.99,
          priceMonthly: 39.99,
          feature: ["2 TB Storage", "10 Users Allowed", "Send up to 20 GB"],
          isCenter: false,
        },
      ],
    };
  },
  methods: {
    toggleTime() {
      this.isMonthly = !this.isMonthly;
    },
  },
});
</script>
