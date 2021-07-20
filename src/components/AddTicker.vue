<template>
  <section>
    <div class="flex">
      <div class="max-w-xs">
        <label class="block text-sm font-medium text-gray-700" for="wallet"
        >Тикер</label
        >
        <div class="mt-1 relative rounded-md shadow-md">
          <input
            id="wallet"
            v-model="ticker"
            class="block w-full pr-10 border-gray-300 text-gray-900 focus:outline-none focus:ring-gray-500 focus:border-gray-500 sm:text-sm rounded-md"
            name="wallet"
            placeholder="Например DOGE"
            type="text"
            @keydown.enter="add"
          />
        </div>
      </div>
    </div>
    <add-button :disabled="disabled" @click="add" type="button" class="my-4" />

  </section>
</template>

<script>
import AddButton from "./AddButton";

export default {
  props: {
    disabled: {
      type: Boolean,
      required: false,
      default: false
    }

  },
  emits: {
    "add-ticker": value => typeof value === "boolean" && value.length > 0
  },
  data() {
    return {
      ticker: ""
    };
  },

  methods: {
    add() {
      if (this.ticker.length === 0) {
        return;
      }
      this.$emit("add-ticker", this.ticker);
      this.ticker = "";
    }
  },

  components: {
    AddButton
  }
};
</script>

<style scoped>

</style>