<template>
  <v-app>
    <v-navigation-drawer app permanent>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            ResaleAI
          </v-list-item-title>
          <v-list-item-subtitle>
            Style Guide
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>
      <v-list dense nav>
        <v-list-item link>
          <v-list-item-content>
            <v-list-item-title>Typography</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app clipped-left>
    </v-app-bar>

    <v-content>
      <Typography/>
      <ScssComponent/>
    </v-content>
  </v-app>
</template>

<script>
import Typography from './components/Typography';
import ScssComponent from './components/ScssComponent';

export default {
  name: 'App',
  components: {
    Typography,
    ScssComponent
  },
  data: () => ({
    //
  }),
};
</script>
