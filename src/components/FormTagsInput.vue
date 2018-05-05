<template>
  <div :class="$options.name">
    <ul
      v-if="tagOptions.length"
      class="list-inline"
    >
      <li
        v-for="tag in tagOptions"
        :key="tag.id"
        class="list-inline-item"
      >
        <button
          class="btn btn-primary btn-sm"
        >
          {{ tag.label }}
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
import formOptionSelectMixin from './mixins/form-option-select-mixin';

export default {
  name: `FormTagsInput`,
  mixins: [formOptionSelectMixin],
  computed: {
    tagOptions() {
      return this.value.map(x => this.optionAdapter(x));
    },
  },
};
</script>
