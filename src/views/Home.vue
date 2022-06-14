<template>
  <div class="home">
    <!--</divimg alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>-->
    <HeaderLux />
    <Hero />
    <Browse class="mb-16" />
    <Arrive />
    <Partner />
    <Aside />
    <Footer />
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'

import HeaderLux from "@/components/HeaderLux.vue";
import Hero from "@/components/Hero.vue";
import Browse from "@/components/Browse.vue";
import Arrive from "@/components/JustArrive.vue";
import Partner from "@/components/Partner.vue";
import Aside from "@/components/Aside.vue";
import Footer from "@/components/Footer";

export default {
  name: "Home",
  components: {
    HeaderLux,
    Hero,
    Browse,
    Arrive,
    Partner,
    Aside,
    Footer,
  },
};
</script>
