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
        <p>
          You've selected:
          {{ simpleMultiValue.length ? simpleMultiValue.join(', ') : 'nothing' }}
        </p>
      </div>
    </section>

    <section :class="`${$options.name}__demo`">
      <h2 class="h3">Single value product selector</h2>
      <form-select
        v-model="singleProduct"
        :options="products"
        :option-adapter="productOptionAdapter"
      />
      <div :class="`${$options.name}__demoFigure`">
        <div :class="`card ${$options.name}__product`">
          <div class="card-body">
            <h5 class="card-title">{{ singleProduct.name }}</h5>
            <p class="card-text">€ {{ singleProduct.price }}</p>
            <a
              href="#"
              class="btn btn-primary"
            >
              Buy me!
            </a>
          </div>
        </div>
      </div>
    </section>

    <section :class="`${$options.name}__demo`">
      <h2 class="h3">Multi value product selector</h2>
      <form-select
        v-model="multiProducts"
        :options="products"
        :option-adapter="productOptionAdapter"
      />
      <div :class="`${$options.name}__demoFigure`">
        <table
          v-if="multiProducts.length"
          class="table"
        >
          <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Price</th>
          </tr>
          <tr
            v-for="product in multiProducts"
            :key="product.uuid"
          >
            <td>{{ product.uuid }}</td>
            <td>{{ product.name }}</td>
            <td>€ {{ product.price }}</td>
          </tr>
        </table>
      </div>
    </section>

    <section :class="`${$options.name}__demo`">
      <h2 class="h3">Multi checkboxes with simple values</h2>
      <form-checkbox
        v-model="simpleCheckboxValue"
        :options="simpleOptions"
      />
      <div :class="`${$options.name}__demoFigure`">
        <p>
          You've selected:
          {{ simpleCheckboxValue.length ? simpleCheckboxValue.join(', ') : 'nothing' }}
        </p>
      </div>
    </section>

    <section :class="`${$options.name}__demo`">
      <h2 class="h3">Multi checkboxe product selector</h2>
      <form-checkbox
        v-model="productsCheckboxValue"
        :options="products"
        :option-adapter="productOptionAdapter"
      />
      <div :class="`${$options.name}__demoFigure`">
        <table
          v-if="productsCheckboxValue.length"
          class="table"
        >
          <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Price</th>
          </tr>
          <tr
            v-for="product in productsCheckboxValue"
            :key="product.uuid"
          >
            <td>{{ product.uuid }}</td>
            <td>{{ product.name }}</td>
            <td>€ {{ product.price }}</td>
          </tr>
        </table>
      </div>
    </section>
  </div>
</template>

<script>
import FormCheckbox from './FormCheckbox.vue';
import FormSelect from './FormSelect.vue';

const products = [
  {
    uuid: `aa11bb`,
    name: `iPad`,
    price: 699,
  },
  {
    uuid: `bb22aa`,
    name: `iPhone`,
    price: 799,
  },
  {
    uuid: `bb33aa`,
    name: `iPhone X`,
    price: 1199,
  },
];

export default {
  name: `App`,
  components: {
    FormCheckbox,
    FormSelect,
  },
  data() {
    return {
      // Simple single value
      simpleValue: null,
      simpleOptions: [`A`, `B`],
      // Simple multi value,
      simpleMultiValue: [],
      // Products
      products,
      singleProduct: products[1],
      multiProducts: [
        products[1],
        products[2],
      ],
      productOptionAdapter(value) {
        return {
          id: value.uuid,
          label: value.name,
          value,
        };
      },
      // Checkbox
      simpleCheckboxValue: [`A`],
      productsCheckboxValue: [],
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

  &__product {
    max-width: 12em;
  }
}
</style>
