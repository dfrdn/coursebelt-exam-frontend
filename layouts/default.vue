<template>
  <div class="flex justify-center bg-gray-200">
    <div class="max-w-screen-lg flex flex-col min-h-screen w-full">
      <NavBar />
      <Buttons />
      <Nuxt class="flex-grow" />
      <Footer />
    </div>
    <div
      hidden
      id="snipcart"
      data-api-key="N2U4M2FmMDEtOWQ4NS00ODE3LWEzNDQtYWU5NTgwNmIwNzNkNjM3MzgxNDczMjk1Mjk2NTEw"
      data-currency="php"
    ></div>
  </div>
</template>

<script>
import NavBar from "./../components/Navbar";
import Footer from "./../components/Footer";
import Buttons from "./../components/Buttons";

export default {
  components: {
    NavBar,
    Footer,
    Buttons,
  },
};
</script>
