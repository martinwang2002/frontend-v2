<template>
  <v-dialog
    v-model="active"
    max-width="400px"
  >
    <template v-slot:activator="{ on, attrs }">
      <v-btn
        v-haptic
        ripple
        text
        outlined
        class="flex-grow-1"
        v-bind="attrs"
        v-on="on"
      >
        <v-icon left>
          mdi-settings
        </v-icon>
        {{ $t('menu.settings.name') }}
      </v-btn>
    </template>
    <v-card :color="`${dark ? 'blue-grey darken-3' : 'white'}`">
      <v-card-title class="headline">
        <v-icon left>
          mdi-settings
        </v-icon>
        {{ $t('menu.settings.name') }}
      </v-card-title>

      <v-card-text>
        <v-container class="pt-0">
          <v-row class="flex-column">
            <Subheader>
              {{ $t('settings.category.appearance') }}
            </Subheader>
            <ThemeSwitcher class="mb-2" />

            <LocaleSwitcher class="mb-2" />

            <OptimizationSwitcher class="mb-2" />

            <DataManager
              v-if="active"
              class="mt-2"
            />
          </v-row>
        </v-container>
      </v-card-text>

      <v-divider />

      <v-card-actions>
        <v-spacer />
        <v-btn
          v-haptic
          text
          @click="active = false"
        >
          {{ $t('meta.dialog.close') }}
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
  import ThemeSwitcher from "@/components/drawer/ThemeSwitcher";
  import LocaleSwitcher from "@/components/drawer/LocaleSwitcher";
  import Theme from "@/mixins/Theme";
  import OptimizationSwitcher from "@/components/drawer/OptimizationSwitcher";
  import DataManager from "@/components/drawer/DataManager";
  import Subheader from "@/components/global/Subheader";
  export default {
    name: "SettingsDialog",
    components: {Subheader, DataManager, OptimizationSwitcher, LocaleSwitcher, ThemeSwitcher},
    mixins: [Theme],
    data() {
      return {
        active: false
      }
    },
  }
</script>

<style scoped>

</style>