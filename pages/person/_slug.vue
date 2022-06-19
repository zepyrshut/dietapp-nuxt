<template>
  <div>
    {{ $route.params.slug }}
    {{ $route.params.id }}

    {{ person }}
  </div>
</template>

<script>
export default {
  name: 'PersonSlug',
  data() {
    return {}
  },

  async asyncData({ app, route }) {
    const client = app.apolloProvider.defaultClient;
    const id = route.params.id;

    const query = {
      query: require("../../graphql/person.gql"),
      variables: { id }
    };

    let person = null
    await client.query(query).then(res => {
      person = res.data.person.data
    })

    return { person }
  },
}

</script>