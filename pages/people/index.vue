<template>

  <div>
    <div v-for="person in people" :key="person.id">
      <v-btn :to="{ path: 'person', name: 'person-slug', params: { slug: person.attributes.slug, id: person.id }, }"
        class="my-1">{{
            person.attributes.name
        }}
      </v-btn>
    </div>
  </div>

</template>

<script>
export default {
  name: 'IndexPeople',
  data() {
    return {}
  },

  async asyncData(context) {
    const client = context.app.apolloProvider.defaultClient;

    const query = {
      query: require("../../graphql/people.gql"),
    }

    let people = []
    await client.query(query).then(res => {
      people = res.data.people.data
    })

    return { people }
  },
}
</script>