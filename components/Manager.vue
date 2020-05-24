<template>
  <div>
    <v-row>
      <v-col cols="12" sm="6" offset-sm="3">
        <v-card>
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
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import Managers from '~/apollo/queries/managers.gql'

export default {
    data() {
        return {
            managers: []
        }
    },

    apollo: {
        managers: {
            query: Managers
        }
    }
}
</script>
