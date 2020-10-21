<template>
  <div class="bg-gray-900">
    <div class="font-sans bg-grey-lighter flex flex-col min-h-screen w-full">
      <div>
        <div class="bg-blue-dark">
          <div class="container mx-auto px-4">
            <div class="flex items-center md:justify-between py-4">
              <div class="w-1/4 md:hidden">
              </div>
              <div
                class="w-1/2 md:w-auto text-center text-white text-2xl font-medium"
              >
                Ghana Stock Exchange
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="flex-grow container mx-auto sm:px-4 pt-6 pb-8">
        <div
          class="bg-gray-900 border-t border-b sm:border-l sm:border-r sm:rounded shadow mb-6"
        >
          <div class="border-b px-6">
            <div class="flex justify-between -mb-px">
              <!-- <div class="lg:hidden text-blue-dark py-4 text-lg">
                Price Charts
              </div> -->
              <div class="hidden lg:flex">
                <h2
                  type="button"
                  class="appearance-none py-4 text-white border-b border-blue-dark mr-6 text-2xl"
                >
                  Live Updates
                </h2>
              </div>
              <div class="flex text-sm"></div>
            </div>
          </div>
          <div
            class="container my-12 mx-auto px-4 md:px-12 text-white"
            v-for="infos in info"
            :key="infos.id"
          >
            <div class="flex flex-wrap -mx-1 lg:-mx-4">
              <!-- Column -->
              <div class="my-1 px-1 w-full md:w-1/2 lg:my-4 lg:px-4 lg:w-1/3">
                <!-- Article -->
                <article class="overflow-hidden rounded-lg shadow-lg">
                  <div class="text-grey-darker mb-2">
                    <span class="text-3xl align-top">{{ infos.name }}</span>
                    <span class="text-5xl">{{ infos.volume }}</span>
                    <span class="text-3xl align-top">.74</span>
                  </div>
                  <div class="text-sm uppercase text-grey tracking-wide">
                    Stocks Volume
                  </div>
                </article>
                <!-- END Article -->
              </div>
              <!-- END Column -->

              <!-- Column -->
              <div class="my-1 px-1 w-full md:w-1/2 lg:my-4 lg:px-4 lg:w-1/3">
                <!-- Article -->
                <article class="overflow-hidden rounded-lg shadow-lg">
                  <div class="text-grey-darker mb-2">
                    <span class="text-3xl align-top"
                      ><span class="text-green align-top"></span>Gh</span
                    >
                    <span class="text-5xl">{{ infos.price }}</span>
                    <!-- <span class="text-3xl align-top">.48</span> -->
                  </div>
                  <div class="text-sm uppercase text-grey tracking-wide">
                    Current Price
                  </div>
                </article>
                <!-- END Article -->
              </div>
              <!-- END Column -->

              <!-- Column -->
              <div class="my-1 px-1 w-full md:w-1/2 lg:my-4 lg:px-4 lg:w-1/3">
                <!-- Article -->
                <article class="overflow-hidden rounded-lg shadow-lg">
                  <div class="text-grey-darker mb-2">
                    <span class="text-3xl align-top"
                      ><span class="text-green align-top">+</span></span
                    >
                    <span class="text-5xl">{{ infos.change }}</span>
                    <span class="text-3xl align-top">Gh</span>
                  </div>

                  <div class="text-sm uppercase text-grey tracking-wide">
                    Since last price Change
                  </div>
                </article>
                <!-- END Article -->
              </div>
              <!-- END Column -->
            </div>
            <hr />
          </div>
        </div>
        <div class="bg-white border-t">
          <div class="container mx-auto px-4">
            <div class="md:flex justify-between items-center text-sm">
              <div
                class="text-center md:text-left py-3 md:py-4 border-b md:border-b-0"
              >
                <a href="#" class="no-underline text-grey-dark"
                  >Legal &amp; Privacy</a
                >
              </div>
              <div class="md:flex md:flex-row-reverse items-center py-4">
                <div class="text-grey text-center md:mr-4">
                  &copy; 2017 Ghana Stock
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      info: null,
    };
  },
  mounted() {
    axios
      .get("https://dev.kwayisi.org/apis/gse/live")
      .then((response) => (this.info = response.data));
  },
};
</script>

<style>
</style>





