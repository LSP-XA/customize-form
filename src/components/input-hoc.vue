<script>
// import ElInput from 'element-ui/packages/input';
// import ElCheckobx from 'element-ui/packages/checkbox';

export default {
  // name: `Wrapped${ElInput.name}`,
  name: 'WrappedInputOrCheckbox',
  // model: ElInput.model,
  props: {
    type: {
      type: String,
      default: 'input',
    },
  },
  computed: {
    comp() {
      return {
        input: () => Promise.all([import('element-ui/lib/input'), import('element-ui/lib/theme-chalk/input.css')]).then(([comp]) => comp),
        checkbox: () => Promise.all([import('element-ui/lib/checkbox'), import('element-ui/lib/theme-chalk/checkbox.css')]).then(([comp]) => comp),
      }[this.type];
    },
  },
  render(h) {
    const model = this.comp.model || {
      prop: 'value',
      event: 'input',
    };
    return h(this.comp, {
      on: {
        ...this.$listeners,
        [model.event]: (e) => {
          this.$emit('input', e);
        },
      },
      attrs: {
        ...this.$attrs,
        [model.prop]: this.$attrs.value,
      },
      scopedSlots: this.$scopedSlots,
    });
  },
};
</script>
