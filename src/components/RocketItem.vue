<script>
import gql from "graphql-tag";
const query = gql`
  query getRocket($id:ID!){
    rocket (id:$id){
      id
      name
      description
      costPerLaunch: cost_per_launch
    }
  }
`;
export default {
  apollo: {
    rocket: {
      query,
      variables(){
        return{ id:this.$route.params.id}
      }
    },
  },
};
</script>

<template>
  <div v-if="rocket">
    <h2>{{rocket.name}}</h2>
    <h3>{{rocket.description}}</h3>
    <h3>{{rocket.costPerLaunch}}</h3>
  </div>
</template>
