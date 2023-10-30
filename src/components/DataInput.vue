<template>
  <div>
    <label
      >Введіть iм'я
      <input type="text" v-model="nameValue" :class="colorName" />
    </label>
    <label
      >Введіть вік
      <input type="number" v-model="ageValue" :class="colorAge" />
    </label>
  </div>
</template>

<script>
export default {
  name: "DataInput",
  data() {
    return {
      colorName: "inValid",
      colorAge: null,
    };
  },
  props: {
    name: {
      type: String,
    },
    nameModifiers: {
      default: () => ({}),
    },
    age: {
      type: Number,
    },
    ageModifiers: {
      default: () => ({}),
    },
  },
  computed: {
    nameValue: {
      get() {
        return this.name;
      },
      set(val) {
        if (val.length < 1 && this.nameModifiers.empty) {
          this.colorName = "inValid";
        } else {
          this.colorName = "static";
        }
        this.$emit("update:name", val);
      },
    },
    ageValue: {
      get() {
        return this.age;
      },
      set(val) {
        if (this.ageModifiers.initColor) {
          if (val.length < 1) this.colorAge = "static";
          else if (val < 18) this.colorAge = "inValid";
          else this.colorAge = "valid";
        }
        this.$emit("update:age", val);
      },
    },
  },
};
</script>

<style lang="css" scoped>
.inValid {
  background-color: red;
}
.valid {
  background-color: green;
}
.static {
  background-color: transparent;
}
</style>