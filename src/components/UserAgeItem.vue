<template>
  <div>
    <label>
      Введіть свій вік :
      <input type="number" v-model="ageValue" :class="colorValue" />
    </label>
  </div>
</template>

<script>
export default {
  name: "UserAgeItem",

  data() {
    return {
      colorValue: null,
    };
  },

  props: {
    modelValue: {
      type: Number,
    },
    modelModifiers: {
      default: () => ({}),
    },
  },

  computed: {
    ageValue: {
      get() {
        return this.modelValue;
      },
      set(val) {
        if (this.modelModifiers.check) {
          if (val >= 150) val = 0;
        }
        if (this.modelModifiers.setColor) {
          this.colorValue = this.validColor(val);
        }
        this.$emit("update:modelValue", val);
      },
    },
  },
  methods: {
    validColor(val) {
      if (val < 10) return "low";
      else if (val <= 21) return "average";
      else return "higher";
    },
  },
};
</script>

<style lang="css" scoped>
.low {
  background-color: green;
}
.average {
  background-color: yellow;
}
.higher {
  background-color: orange;
}
</style>