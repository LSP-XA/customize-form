<template>
  <el-input :value="value" @input="$emit('input', $event)" />
</template>

<script>
export default {
  props: {
    value: String,
  },
};
</script>
