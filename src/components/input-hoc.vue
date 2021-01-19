<script>
import ElInput from 'element-ui/packages/input';

export default {
  name: `Wrapped${ElInput.name}`,
  render(h) {
    return h(ElInput, {
      on: this.$listeners,
      attrs: this.$attrs,
      scopedSlots: this.$scopedSlots,
    });
  },
};
</script>
