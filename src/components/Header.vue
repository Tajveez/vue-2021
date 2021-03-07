<template>
  <header>
    <h1>
      {{ title }}
    </h1>
    <Button
      @toggle-form="$emit('toggle-form')"
      :color="btnColor"
      :text="btnText"
    />
  </header>
</template>

<script>
import Button from "./Button";
export default {
  name: "Header",
  props: {
    title: String,
    btnText: String,
    btnColor: String,
  },
  components: {
    Button,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
