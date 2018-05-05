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
      v-for="option in adaptedOptions"
      :key="option.id"
      :value="option.id"
      v-text="option.label"
    />
  </select>
</template>

<script>
import formOptionSelectMixin from './mixins/form-option-select-mixin';

export default {
  name: `FormSelect`,
  mixins: [formOptionSelectMixin],
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
  },
};
</script>
