<template>
  <button @click="handleClick()" class="btn" :style="{ background: color }">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: String,
    color: String,
  },
  methods: {
    handleClick() {
      this.$emit("btn-click");
    },
  },
};
</script>
