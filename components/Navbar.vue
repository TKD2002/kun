<template>
  <div
    class="rounded bg-gray-200 px-4 py-5 mx-auto sm:max-w-xl md:max-w-full lg:max-w-screen-xl md:px-24 lg:px-8"
  >
    <div class="relative flex items-center justify-between">
      <div class="flex items-center">
        <ul class="flex items-center hidden space-x-8 lg:flex">
          <li>
            <a
              href="/"
              class="font-medium tracking-wide text-gray-700 transition-colors duration-200 hover:text-purple-400"
              >Product</a
            >
          </li>
          <li>
            <a
              href="/profile"
              class="font-medium tracking-wide text-gray-700 transition-colors duration-200 hover:text-purple-400"
              >Profile</a
            >
          </li>
          <li>
            <a
              href="https://github.com/TKD2002"
              class="font-medium tracking-wide text-gray-700 transition-colors duration-200 hover:text-purple-400"
              >Github</a
            >
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isMenuOpen: false,
    };
  },
};
</script>