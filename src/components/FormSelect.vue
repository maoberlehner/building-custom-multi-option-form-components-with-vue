<template>
  <select
    :class="$options.name"
    :multiple="multiple"
    v-model="selected"
    @change="updateValue"
  >
    <option
      disabled
      value=""
      v-text="disabledOption"
    />
    <option
      v-for="option in options"
      :key="option"
      :value="option"
      v-text="option"
    />
  </select>
</template>

<script>
export default {
  name: `FormSelect`,
  model: {
    // By default, `v-model` reacts to the `input`
    // event for updating the value, we change this
    // to `change` for similar behavior as the
    // native `<select>` element.
    event: `change`,
  },
  props: {
    // The disabled option is necessary because
    // otherwise it isn't possible to select the
    // first item on iOS devices. This prop can
    // be used to configure the text for the
    // disabled option.
    disabledOption: {
      type: String,
      default: `Select something`,
    },
    options: {
      type: Array,
      default: () => [],
    },
    value: {
      type: [Array, String, Number],
      default: null,
    },
  },
  data() {
    return {
      selected: this.value,
    };
  },
  computed: {
    multiple() {
      return Array.isArray(this.value);
    },
  },
  methods: {
    updateValue() {
      // Emitting a `change` event with the new
      // value of the `<select>` field, updates
      // all values bound with `v-model`.
      this.$emit(`change`, this.selected);
    },
  },
};
</script>
