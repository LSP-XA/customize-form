<script>
import ElInput from 'element-ui/packages/checkbox';

export default {
  name: `Wrapped${ElInput.name}`,
  model: ElInput.model,
  render(h) {
    return h(ElInput, {
      on: this.$listeners,
      attrs: this.$attrs,
      scopedSlots: this.$scopedSlots,
    });
  },
};
</script>
