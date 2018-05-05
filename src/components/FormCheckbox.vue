<template>
  <div :class="$options.name">
    <div
      v-for="option in adaptedOptions"
      :key="option.id"
      :class="`${$options.name}__option`"
    >
      <label>
        <input
          :class="`${$options.name}__input`"
          :value="option.id"
          v-model="selected"
          type="checkbox"
          @change="updateValue"
        >
        {{ option.label }}
      </label>
    </div>
  </div>
</template>

<script>
import formOptionSelectMixin from './mixins/form-option-select-mixin';

export default {
  name: `FormCheckbox`,
  mixins: [formOptionSelectMixin],
};
</script>
