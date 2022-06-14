<template>
  <div class="home">
    <!--</divimg alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <HeaderLux />
    <!-- START: BREADCRUMB -->
    <section class="bg-gray-100 py-8 px-4">
      <div class="container mx-auto">
        <ul class="breadcrumb">
          <li>
            <router-link to="/">Home</router-link>
          </li>
          <li>
            <a href="#" aria-label="current-page">Shopping Cart</a>
          </li>
        </ul>
      </div>
    </section>
    <!-- END: BREADCRUMB -->

    <!-- START: COMPLETE YOUR ROOM -->
    <section class="md:py-16">
      <div class="container mx-auto px-4">
        <div class="flex -mx-4 flex-wrap">
          <div class="w-full px-4 mb-4 md:w-8/12 md:mb-0" id="shopping-cart">
            <div
              class="
                flex flex-start
                mb-4
                mt-8
                pb-3
                border-b border-gray-200
                md:border-b-0
              "
            >
              <h3 class="text-2xl">Shopping Cart</h3>
            </div>

            <div class="border-b border-gray-200 mb-4 hidden md:block">
              <div class="flex flex-start items-center pb-2 -mx-4">
                <div class="px-4 flex-none">
                  <div class="" style="width: 90px">
                    <h6>Photo</h6>
                  </div>
                </div>
                <div class="px-4 w-5/12">
                  <div class="">
                    <h6>Product</h6>
                  </div>
                </div>
                <div class="px-4 w-5/12">
                  <div class="">
                    <h6>Price</h6>
                  </div>
                </div>
                <div class="px-4 w-2/12">
                  <div class="text-center">
                    <h6>Action</h6>
                  </div>
                </div>
              </div>
            </div>
            <div v-if="keranjangUser.length > 0">
              <div v-for="item in keranjangUser" :key="item.id">
                <div
                  class="flex flex-start flex-wrap items-center mb-4 -mx-4"
                  data-row="1"
                >
                  <div class="px-4 flex-none">
                    <div class="" style="width: 90px; height: 90px">
                      <img
                        :src="item.photo"
                        alt="chair-1"
                        class="object-cover rounded-xl w-full h-full"
                      />
                    </div>
                  </div>
                  <div class="px-4 w-auto flex-1 md:w-5/12">
                    <div class="">
                      <h6 class="font-semibold text-lg md:text-xl leading-8">
                        {{ item.name }}
                      </h6>
                      <span class="text-sm md:text-lg">{{ item.type }}</span>
                      <h6
                        class="
                          font-semibold
                          text-base
                          md:text-lg
                          block
                          md:hidden
                        "
                      >
                        IDR {{ item.price }}
                      </h6>
                    </div>
                  </div>
                  <div
                    class="
                      px-4
                      w-auto
                      flex-none
                      md:flex-1 md:w-5/12
                      hidden
                      md:block
                    "
                  >
                    <div class="">
                      <h6 class="font-semibold text-lg">
                        IDR {{ item.price }}
                      </h6>
                    </div>
                  </div>
                  <div class="px-4 w-2/12">
                    <div class="text-center">
                      <button
                        @click="removeItem(item.id)"
                        data-delete-item="1"
                        class="
                          text-red-600
                          border-none
                          focus:outline-none
                          px-3
                          py-1
                        "
                      >
                        X
                      </button>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div v-else>
              <p class="text-center py-8">
                Ooops... Cart is empty
                <a href="details.html" class="underline">Shop Now</a>
              </p>
            </div>
          </div>
          <div class="w-full md:px-4 md:w-4/12" id="shipping-detail">
            <div class="bg-gray-100 px-4 py-6 md:p-8 md:rounded-3xl">
              <form>
                <div class="flex flex-start mb-6">
                  <h3 class="text-2xl">Shipping Details</h3>
                </div>

                <div class="flex flex-col mb-4">
                  <label for="complete-name" class="text-sm mb-2"
                    >Complete Name</label
                  >
                  <input
                    data-input
                    type="text"
                    id="complete-name"
                    class="
                      border-gray-200 border
                      rounded-lg
                      px-4
                      py-2
                      bg-white
                      text-sm
                      focus:border-blue-200 focus:outline-none
                    "
                    placeholder="Input your name"
                    v-model="customerInfo.name"
                  />
                </div>

                <div class="flex flex-col mb-4">
                  <label for="email" class="text-sm mb-2">Email Address</label>
                  <input
                    data-input
                    type="email"
                    id="email"
                    class="
                      border-gray-200 border
                      rounded-lg
                      px-4
                      py-2
                      bg-white
                      text-sm
                      focus:border-blue-200 focus:outline-none
                    "
                    placeholder="Input your email address"
                    v-model="customerInfo.email"
                  />
                </div>

                <div class="flex flex-col mb-4">
                  <label for="address" class="text-sm mb-2">Address</label>
                  <input
                    data-input
                    type="text"
                    id="address"
                    class="
                      border-gray-200 border
                      rounded-lg
                      px-4
                      py-2
                      bg-white
                      text-sm
                      focus:border-blue-200 focus:outline-none
                    "
                    placeholder="Input your address"
                    v-model="customerInfo.address"
                  />
                </div>

                <div class="flex flex-col mb-4">
                  <label for="phone-number" class="text-sm mb-2"
                    >Phone Number</label
                  >
                  <input
                    data-input
                    type="tel"
                    id="phone-number"
                    class="
                      border-gray-200 border
                      rounded-lg
                      px-4
                      py-2
                      bg-white
                      text-sm
                      focus:border-blue-200 focus:outline-none
                    "
                    placeholder="Input your phone number"
                    v-model="customerInfo.number"
                  />
                </div>

                <div class="flex flex-col mb-4">
                  <label for="complete-name" class="text-sm mb-2"
                    >Choose Courier</label
                  >
                  <div class="flex -mx-2 flex-wrap">
                    <div class="px-2 w-6/12 h-24 mb-4">
                      <button
                        type="button"
                        data-value="fedex"
                        data-name="courier"
                        class="
                          border border-gray-200
                          focus:border-red-200
                          flex
                          items-center
                          justify-center
                          rounded-xl
                          bg-white
                          w-full
                          h-full
                          focus:outline-none
                        "
                      >
                        <img
                          src="../assets/content/logo-fedex.svg"
                          alt="Logo Fedex"
                          class="object-contain max-h-full"
                        />
                      </button>
                    </div>
                    <div class="px-2 w-6/12 h-24 mb-4">
                      <button
                        type="button"
                        data-value="dhl"
                        data-name="courier"
                        class="
                          border border-gray-200
                          focus:border-red-200
                          flex
                          items-center
                          justify-center
                          rounded-xl
                          bg-white
                          w-full
                          h-full
                          focus:outline-none
                        "
                      >
                        <img
                          src="../assets/content/logo-dhl.svg"
                          alt="Logo dhl"
                          class="object-contain max-h-full"
                        />
                      </button>
                    </div>
                  </div>
                </div>

                <div class="flex flex-col mb-4">
                  <label for="complete-name" class="text-sm mb-2"
                    >Choose Payment</label
                  >
                  <div class="flex -mx-2 flex-wrap">
                    <div class="px-2 w-6/12 h-24 mb-4">
                      <input
                        type="radio"
                        name="payment"
                        id="midtrans"
                        class="hidden"
                      />
                      <label for="midtrans">
                        <button
                          type="button"
                          data-value="midtrans"
                          data-name="payment"
                          class="
                            border border-gray-200
                            focus:border-red-200
                            flex
                            items-center
                            justify-center
                            rounded-xl
                            bg-white
                            w-full
                            h-full
                            focus:outline-none
                          "
                        >
                          <img
                            src="../assets/content/logo-midtrans.png"
                            alt="Logo midtrans"
                            class="object-contain max-h-full"
                          />
                        </button>
                      </label>
                    </div>
                    <div class="px-2 w-6/12 h-24 mb-4">
                      <input
                        type="radio"
                        name="payment"
                        id="mastercard"
                        class="hidden"
                      />
                      <label for="mastercard">
                        <button
                          type="button"
                          data-value="midtrans"
                          data-name="payment"
                          class="
                            border border-gray-200
                            focus:border-red-200
                            flex
                            items-center
                            justify-center
                            rounded-xl
                            bg-white
                            w-full
                            h-full
                            focus:outline-none
                          "
                        >
                          <img
                            src="../assets/content/logo-mastercard.svg"
                            alt="Logo mastercard"
                          />
                        </button>
                      </label>
                    </div>
                    <div class="px-2 w-6/12 h-24 mb-4">
                      <button
                        type="button"
                        data-value="bitcoin"
                        data-name="payment"
                        class="
                          border border-gray-200
                          focus:border-red-200
                          flex
                          items-center
                          justify-center
                          rounded-xl
                          bg-white
                          w-full
                          h-full
                          focus:outline-none
                        "
                      >
                        <img
                          src="../assets/content/logo-bitcoin.svg"
                          alt="Logo bitcoin"
                          class="object-contain max-h-full"
                        />
                      </button>
                    </div>
                    <div class="px-2 w-6/12 h-24 mb-4">
                      <button
                        type="button"
                        data-value="american-express"
                        data-name="payment"
                        class="
                          border border-gray-200
                          focus:border-red-200
                          flex
                          items-center
                          justify-center
                          rounded-xl
                          bg-white
                          w-full
                          h-full
                          focus:outline-none
                        "
                      >
                        <img
                          src="../assets/content/logo-american-express.svg"
                          alt="Logo american-logo-american-express"
                        />
                      </button>
                    </div>
                  </div>
                </div>
              </form>
              <div class="text-center">
                <a
                  type="submit"
                  class="
                    bg-pink-400
                    text-black
                    hover:bg-black hover:text-pink-400
                    focus:outline-none
                    w-full
                    py-3
                    rounded-full
                    text-lg
                    focus:text-black
                    transition-all
                    duration-200
                    px-6
                  "
                  @click="checkout()"
                >
                  Checkout Now
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!-- END: COMPLETE YOUR ROOM -->
    <Aside />
    <Footer />
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'

import HeaderLux from "@/components/HeaderLux.vue";
import Aside from "@/components/Aside.vue";
import Footer from "@/components/Footer";
import axios from "axios";

export default {
  name: "Cart",
  components: {
    HeaderLux,
    Aside,
    Footer,
  },
  data() {
    return {
      keranjangUser: [],
      customerInfo: {
        name: "",
        email: "",
        number: "",
        address: "",
        price: "",
      },
    };
  },
  methods: {
    moveUp() {
      window.scrollTo(0, 0);
    },
    removeItem(itemId) {
      //mencari nilai id dari item yang ingin dihapus
      let keranjangUserStorage = JSON.parse(
        localStorage.getItem("keranjangUser")
      );
      let itemKeranjangUserStorage = keranjangUserStorage.map(
        (itemKeranjangUserStorage) => itemKeranjangUserStorage.id
      );
      //cocokan id yang ditemukan dengan itemId
      let index = itemKeranjangUserStorage.findIndex((id) => id == itemId);
      this.keranjangUser.splice(index, 1);
      //simpan di local storage
      const parsed = JSON.stringify(this.keranjangUser);
      localStorage.setItem("keranjangUser", parsed);
      window.location.reload();
    },
    checkout() {
      let productIds = this.keranjangUser.map(function (product) {
        return product.id;
      });

      let checkoutData = {
        name: this.customerInfo.name,
        email: this.customerInfo.email,
        number: this.customerInfo.number,
        address: this.customerInfo.address,
        transaction_total: this.totalHarga,
        transaction_status: "PENDING",
        transaction_details: productIds,
      };
      axios
        .post("https://admin.luxspace.my.id/api/checkout", checkoutData)
        .then(() => this.$router.push("success"))
        .catch((err) => console.log(err));
      localStorage.clear();
    },
  },
  mounted() {
    if (localStorage.getItem("keranjangUser")) {
      try {
        this.keranjangUser = JSON.parse(localStorage.getItem("keranjangUser"));
      } catch (e) {
        localStorage.removeItem("keranjangUser");
      }
    }
  },
  computed: {
    totalHarga() {
      return this.keranjangUser.reduce(function (items, data) {
        return items + data.price;
      }, 0);
    },
  },
};
</script>
