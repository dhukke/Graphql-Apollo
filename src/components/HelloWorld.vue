<template>
  <v-container>
    <v-row dense v-for="pizza in pizzas" :key="pizza.id">
      <v-col cols="12">
        <v-card hover elevation="2" outlined shaped>
          <v-card-title>
            <h2>{{ pizza.name }}</h2>
          </v-card-title>
          <v-card-text> Topping: {{ pizza.topping.name }} </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
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
};
</script>
