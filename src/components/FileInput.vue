<template>
  <div>
    <label>
      Введіть шлях до файлу з розширенням .js
      <input type="text" v-model="valueFile" :class="colorInput" />
    </label>
    <button :disabled="isDisabledBtn">Add</button>
  </div>
</template>



<script>
export default {
  name: "FileInput",
  data() {
    return {
      colorInput: null,
      isDisabledBtn: true,
    };
  },
  props: {
    modelValue: {
      type: String,
    },
    modelModifiers: {
      default: () => ({}),
    },
  },
  computed: {
    valueFile: {
      get() {
        return this.modelValue;
      },
      set(val) {
        if (this.isValidValue(val)) {
          this.isDisabledBtn = false;
        }
        if (this.isValidValue(val) && this.modelModifiers.checkPath) {
          this.colorInput = "valid";
        } else this.colorInput = "notValid";

        this.$emit("update:modelValue", val);
      },
    },
  },
  methods: {
    isValidValue(val) {
      return /.+\.js$/.test(val);
    },
  },
};
</script>

<style lang="css" scoped>
.notValid {
  background-color: red;
}
.valid {
  background-color: none;
}
</style>