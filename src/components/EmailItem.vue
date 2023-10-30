<template>
  <div>
    <label>
      Введіть e-mail
      <input
        type="email"
        ref="input"
        v-model.lazy="valueEmail"
        :class="colorInput"
      />@inv.mn.edu
    </label>
  </div>
</template>

<script>
const emailDomen = "@inv.mn.edu";
export default {
  name: "EmailItem",

  data() {
    return {
      colorInput: null,
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
    valueEmail: {
      get() {
        return this.modelValue;
      },
      set(val) {
        if (this.isValidEmail(val) && this.modelModifiers.check) {
          val = val + emailDomen;
          this.colorInput = "valid";
        } else this.colorInput = "inValid";

        this.$emit("update:modelValue", val);
      },
    },
  },
  methods: {
    isValidEmail(val) {
      return /^[a-zA-Z]+[-_A-Z]+[a-zA-Z]/.test(val);
    },
  },
};
</script>

<style lang="css" scoped>
.valid {
  background-color: greenyellow;
}
.inValid {
  background-color: red;
}
</style>