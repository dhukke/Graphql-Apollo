<template>
  <div class="hello">
    <div v-for="pizza in pizzas" :key="pizza.id">
      {{ pizza.name }}
      <div>
        {{ pizza.topping.name }}
      </div>
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag';

export default {
  name: 'HelloWorld',
  apollo: {
    pizzas: gql`
      query {
        pizzas(where: { topping: { name: { contains: "First Topping" } } }) {
          id
          name
          topping {
            name
          }
        }
      }
    `,
  },
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
