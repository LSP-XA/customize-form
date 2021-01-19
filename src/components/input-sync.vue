<template>
  <el-input :value="value" @input="$emit('update:value', $event)" />
</template>

<script>
export default {
  props: {
    value: String,
  },
};
</script>
