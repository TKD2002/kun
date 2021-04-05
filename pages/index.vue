<template>
  <div>
    <div
      class="px-4 py-16 mx-auto sm:max-w-xl md:max-w-full lg:max-w-screen-xl md:px-24 lg:px-8 lg:py-20"
    >
      <div
        class="max-w-xl mb-6 sm:mx-auto sm:text-center md:mb-10 lg:max-w-2xl"
      >
        <p class="mb-1 text-xs font-semibold tracking-wide uppercase md:mb-2">
          Best Places to Buy Seafood Online
        </p>
        <p class="text-base text-gray-700 md:text-lg">
          In order to minimize frequent trips to the grocery store, people are
          turning to the web more and more for online retailers that deliver
          straight to their doorstep. Now, it's possible to get practically
          anything you want sent on-demand, including high quality fresh and
          frozen seafood. To make the process smoother for you, we've compiled a
          list of the top seafood retailers in the country that are providing
          home delivery of fish that is even fresher than what is typically
          found in a grocery store.
        </p>
      </div>
    </div>
    <div>
      <h2
        class="text-center max-w-lg mb-6 font-sans text-3xl font-bold leading-none tracking-tight text-gray-900 sm:text-4xl md:mx-auto"
      >
        Products
      </h2>
      <div>
        <div class="container text-center p-50">
          <div class="row"></div>

          <div class="row flex p-10 bg-white">
            <div
              class="card px-10 p-10 hover:shadow-xl duration-3 size-105"
              v-for="product in products"
              :key="product.id.toString()"
            >
              <div>
                <img :src="product.img" alt="" />
                {{ product.name }}
                <div class="card">Price: {{ product.price }}</div>

                <button
                  v-if="!product.cart"
                  @click="add(product)"
                  href="#"
                  class="bg-purple-500 p-5 text-white"
                >
                  Add to Cart
                </button>
                <button
                  v-if="product.cart"
                  @click="add(product)"
                  :disabled="product.cart"
                  href="#"
                  class="bg-purple-200 p-5 text-gray-900 bodered"
                >
                  Product Added to Cart
                </button>
              </div>
            </div>
          </div>
        </div>
        <div>
          <div class="row">
            <div
              class="flex flex-col text-base text-gray-700 md:text-lg text-center"
            >
              <h2>Shopping Cart</h2>
            </div>
          </div>
          <table style="margin-left: 500px">
            <thead class="flex px-10 text-center">
              <td class="p-5">#</td>
              <td class="p-5">Quantity</td>
              <td class="p-5">Price</td>
              <td class="p-5">Product Name</td>
            </thead>
            <tbody>
              <tr
                v-for="(p, idx) in cart"
                :key="p.id.toString()"
                class="flex p-5"
              >
                <td class="p-5">{{ idx + 1 }}</td>
                <td class="flex flex-inline">
                  <button
                    class="bg-gray-500 p-2 text-white flex-1"
                    @click="increment(p.id)"
                  >
                    +
                  </button>
                  <div class="flex flex-2 pt-5 p-3">{{ p.quantity }}</div>
                  <button
                    class="bg-purple-500 p-2 text-white flex-3"
                    @click="decrement(p.id)"
                  >
                    -
                  </button>
                </td>
                <td class="p-5">{{ p.price }}</td>
                <td class="p-5">{{ p.name }}</td>
              </tr>
            </tbody>
          </table>
          <div style="margin-left: 500px">
            <h4 class="text-center">Total : {{ total }}</h4>
            <button class="p-3 bg-gray-200" @click="buy">Buy</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Cart",
  props: {
    msg: String,
  },
  data() {
    return {
      ticket: {
        products: null,
        total: 0,
      },
      counter: 0,
      products: [
        {
          id: 1,
          img: require("@/assets/shell1.jpg"),
          name: "PLittle Gun Oysters",
          price: 9.99,
          cart: false,
          quantity: 1,
        },
        {
          id: 2,
          img: require("@/assets/shell2.jpg"),
          name: "Moondancer Oysters",
          price: 10.99,
          cart: false,
          quantity: 1,
        },
        {
          id: 3,
          img: require("@/assets/shell3.jpg"),
          name: "Moondancer Oysters, Box",
          price: 19.99,
          cart: false,
          quantity: 1,
        },
        {
          id: 4,
          img: require("@/assets/shell4.jpg"),
          name: "Shucked Oysters",
          price: 2.99,
          cart: false,
          quantity: 1,
        },
      ],
      cart: [],
      fields: ["#", "remove", "name", "quantity", "price"],
    }; // data return
  },
  methods: {
    add(product) {
      this.products[product.id - 1].cart = true;
      this.cart.push(product);
      // this.counter++;
    },
    increment(id) {
      const idx = this.cart.findIndex((c) => c.id === id);
      this.cart[idx].quantity++;
    },
    decrement(id) {
      const idx = this.cart.findIndex((c) => c.id === id);
      if (this.cart[idx].quantity <= 0) return;
      this.cart[idx].quantity--;
    },
    buy() {
      alert("Purchase Complete");
    },
  },
  computed: {
    total() {
      let t = 0;
      for (let index = 0; index < this.cart.length; index++) {
        t += this.cart[index].price * this.cart[index].quantity;
      }
      return t.toFixed(2);
    },
  },
};
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
