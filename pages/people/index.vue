<template>
  <v-container>
    <v-text-field v-model="search" append-icon="mdi-magnify" label="Buscar" hide-details></v-text-field>
    <v-data-table :headers="headers" :items="people" item-key="id" :search="search">
      <template v-slot:item.controls="props">
        <a @click="onButtonClick(props.item.attributes.slug, props.item.id)">
          <v-icon class="hoverable">mdi-pencil-outline</v-icon>
        </a>
      </template>
    </v-data-table>
  </v-container>
</template>

<script>
export default {
  name: 'IndexPeople',
  data() {
    return {
      search: '',
      headers: [
        {
          text: 'Nombre',
          value: 'attributes.name',
        },
        {
          text: 'Apellido',
          value: 'attributes.lastname',
        },
        {
          text: 'Alias',
          value: 'attributes.slug',
        },
        {
          text: '',
          value: 'controls',
          sortable: false
        }
      ]
    }
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

  methods: {
    onButtonClick(slug, id) {
      console.log(slug)
      this.$router.push({ path: 'person', name: 'person-slug', params: { slug, id } })

    }
  }
}
</script>

<style>
.hoverable:hover {
  color: #cc8e35;
}
</style>