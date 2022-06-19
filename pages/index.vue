<template>
  <v-container>
    <v-btn class="primary">primary</v-btn>
    <v-btn class="accent">accent</v-btn>
    <v-btn class="secondary">secondary</v-btn>
    <v-btn class="info">info</v-btn>
    <v-btn class="warning">warning</v-btn>
    <v-btn class="error">error</v-btn>
    <v-btn class="success">success</v-btn>
    <v-btn class="disabled">disabled</v-btn>


    <v-card class="mx-auto" width="300">
      <v-list>
        <v-list-item>
          <v-list-item-icon>
            <v-icon>mdi-home</v-icon>
          </v-list-item-icon>

          <v-list-item-title>Home</v-list-item-title>
        </v-list-item>

        <v-list-group :value="true" prepend-icon="mdi-account-circle">
          <template v-slot:activator>
            <v-list-item-title>Users</v-list-item-title>
          </template>



          <v-list-item v-for="([title, icon], i) in admins" :key="i" link>
            <v-list-item-title v-text="title"></v-list-item-title>

            <v-list-item-icon>
              <v-icon v-text="icon"></v-icon>
            </v-list-item-icon>
          </v-list-item>


          <v-list-group no-action sub-group>
            <template v-slot:activator>
              <v-list-item-content>
                <v-list-item-title>Actions</v-list-item-title>
              </v-list-item-content>
            </template>

            <v-list-item v-for="([title, icon], i) in cruds" :key="i" link>
              <v-list-item-title v-text="title"></v-list-item-title>

              <v-list-item-icon>
                <v-icon v-text="icon"></v-icon>
              </v-list-item-icon>
            </v-list-item>
          </v-list-group>
        </v-list-group>
      </v-list>
    </v-card>

  </v-container>
</template>

<script>
export default {
  name: 'IndexPage',
  data: () => ({
    admins: [
      ['Management', 'mdi-account-multiple-outline'],
      ['Settings', 'mdi-cog-outline'],
    ],
    cruds: [
      ['Create', 'mdi-plus-outline'],
      ['Read', 'mdi-file-outline'],
      ['Update', 'mdi-update'],
      ['Delete', 'mdi-delete'],
    ],
  }),
}
</script>
