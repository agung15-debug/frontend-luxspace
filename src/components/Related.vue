<template>
  <!-- START: COMPLETE YOUR ROOM -->
  <section class="bg-gray-100 px-4 py-16">
    <div class="container mx-auto">
      <div class="flex flex-start mb-4 text-left">
        <h3 class="text-2xl capitalize font-semibold">
          Complete your room <br class="" />with what we designed
        </h3>
      </div>
      <div class="flex overflow-x-auto mb-4 -mx-3">
        <div
          v-for="item in items"
          :key="item.id"
          class="px-3 flex-none"
          style="width: 320px"
        >
          <div class="rounded-xl p-4 pb-8 relative bg-white">
            <div class="rounded-xl overflow-hidden card-shadow w-full h-36">
              <img
                :src="require('@/assets/content/' + item.photo)"
                alt=""
                class="w-full h-full object-cover object-center"
              />
            </div>
            <h5 class="text-lg font-semibold mt-4">{{ item.productName }}</h5>
            <span class="">{{ item.price }}</span>
            <router-link to="/product" class="stretched-link" @click="moveUp">
              <!-- fake children -->
            </router-link>
          </div>
        </div>
      </div>
    </div>
  </section>
  <!-- END: COMPLETE YOUR ROOM -->
</template>
<script>
export default {
  name: "Related",
  data() {
    return {
      items: [
        {
          id: 1,
          photo: "chair-1.png",
          productName: "Cangkir Mauttie",
          price: "IDR 89.300.000",
        },
        {
          id: 2,
          photo: "chair-2.png",
          productName: "Saman Kakka",
          price: "IDR 14.500.399",
        },
        {
          id: 3,
          photo: "chair-3.png",
          productName: "Lino Dino",
          price: "IDR 22.000.000",
        },
        {
          id: 4,
          photo: "chair-1.png",
          productName: "Syail Ammeno",
          price: "IDR 6.399.999",
        },
      ],
    };
  },
  methods: {
    moveUp() {
      window.scrollTo(0, 0);
    },
  },
};
</script>
