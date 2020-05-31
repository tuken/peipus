<template>
  <v-layout column justify-center align-center>
    <v-card v-if="managers">
      <v-card-title>
        管理アカウント一覧
        <v-spacer />
        <v-text-field v-model="search" append-icon="mdi-magnify" label="検索" sigle-line />
      </v-card-title>
      <v-data-table :headers="headers" :items="managers" :items-per-page="5" :search="search" class="elevation-1">
        <template v-slot:item.actions="{ item }">
          <v-icon small @click="edit(item)">
            mdi-pencil
          </v-icon>
          <v-icon small @click="remove(item)">
            mdi-delete
          </v-icon>
        </template>
      </v-data-table>
    </v-card>
  </v-layout>
  <!-- <div>
    <v-row>
      <v-col cols="12" sm="6" offset-sm="3">
        <v-data-table>
          <v-list two-line subheader>
            <v-list-item v-for="item in managers" :key="item.id" link>
              <v-list-item-avatar>
                <v-icon>mdi-gift-outline</v-icon>
              </v-list-item-avatar>
              <v-list-item-content>
                <v-list-item-title>{{ item.email }}</v-list-item-title>
                <v-list-item-subtitle>{{ item.firstName }}</v-list-item-subtitle>
              </v-list-item-content>
              <v-list-item-content>
                <v-list-item-title>
                  {{ item.lastName }}
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-data-table>
      </v-col>
    </v-row>
  </div> -->
</template>

<script>
import Managers from '~/apollo/queries/managers.gql'

export default {
  data() {
    return {
      headers: [
        { text: 'ID', value: 'id' },
        { text: 'メールアドレス', value: 'email' },
        { text: '姓', value: 'lastName' },
        { text: '名', value: 'firstName' },
        { text: '操作', value: 'actions' }
      ],
      managers: {
        managers: []
      }
    }
  },
  apollo: {
    managers: {
      query: Managers
    }
  }
}
</script>
