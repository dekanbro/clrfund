<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawerRight" app clipped right>
      <v-list dense>
        <v-list-item>
          <v-avatar size="100">
            <v-img :src="selectedRecpient.avatar"></v-img>
          </v-avatar>
        </v-list-item>
        <v-list-item-title
          >Recpient: {{ selectedRecpient.title }}</v-list-item-title
        >
        <v-list-item-content>
          {{ selectedRecpient.description }}
        </v-list-item-content>
      </v-list>
    </v-navigation-drawer>

    <v-navigation-drawer v-model="drawer" app>
      <v-list dense>
        <v-list-item link @click="$router.push('/')">
          <v-list-item-action>
            <v-avatar size="100">
              <v-img src="https://i.imgur.com/h7mX6I0.png"></v-img>
            </v-avatar>
          </v-list-item-action>
        </v-list-item>
        <v-list-item>
          Cl(ea)r.Fund
        </v-list-item>
        <RoundList />
      </v-list>
    </v-navigation-drawer>

    <v-navigation-drawer v-model="left" fixed temporary></v-navigation-drawer>

    <v-main>
      <router-view @selectRecipient="onSelectRecipientChild"></router-view>
      <v-btn color="pink" dark large absolute bottom right fab>
        <v-icon>mdi-check</v-icon>
      </v-btn>
    </v-main>

    <v-navigation-drawer
      v-model="right"
      fixed
      right
      temporary
    ></v-navigation-drawer>

    <v-footer app color="white" class="white--text">
      <span>Cl(ea)r.Fund</span>
      <v-spacer></v-spacer>
      <span>&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
import RoundList from "./components/RoundList";

export default {
  components: {
    RoundList,
  },
  props: {
    source: String,
  },

  data: () => ({
    drawer: null,
    drawerRight: null,
    right: false,
    left: false,
    selectedRecpient: {},
  }),
  methods: {
    onSelectRecipientChild(recipient) {
      console.log("on recipient", recipient);
      this.selectedRecpient = recipient;
    },
  },
  created() {
    this.$vuetify.theme.dark = true;
  }
};
</script>
