<template>
  <div :class="$options.name">
    <h1 class="h2">Vue.js Multi-Option Form Components</h1>

    <section :class="`${$options.name}__demo`">
      <h2 class="h3">Simple single value selection</h2>
      <form-select
        v-model="simpleValue"
        :options="simpleOptions"
      />
      <div :class="`${$options.name}__demoFigure`">
        <p>You've selected: {{ simpleValue || 'nothing' }}</p>
      </div>
    </section>

    <section :class="`${$options.name}__demo`">
      <h2 class="h3">Simple multi value selection</h2>
      <form-select
        v-model="simpleMultiValue"
        :options="simpleOptions"
      />
      <div :class="`${$options.name}__demoFigure`">
        <p>You've selected: {{ simpleMultiValue.length ? simpleMultiValue.join(', ') : 'nothing' }}</p>
      </div>
    </section>
  </div>
</template>

<script>
import FormSelect from './FormSelect.vue';

export default {
  name: `App`,
  components: {
    FormSelect,
  },
  data() {
    return {
      // Simple single value
      simpleValue: null,
      simpleOptions: [`A`, `B`],
      // Simple multi value,
      simpleMultiValue: [],
    };
  },
};
</script>

<style lang="scss">
@import '~bootstrap/scss/bootstrap.scss';

body {
  margin-right: auto;
  margin-left: auto;
  padding: 1em;
  max-width: 42em;
}

.App {
  &__demo {
    margin-top: 3em;

    h2 {
      margin-bottom: 0.75em;
    }
  }

  &__demoFigure {
    margin-top: 1em;
  }
}
</style>
