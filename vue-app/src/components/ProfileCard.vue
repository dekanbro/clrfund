<template>
  <v-row>
    <v-col cols="2">
      <v-avatar size="40" v-if="profile.image">
        <v-img
          :src="
            'https://ipfs.infura.io/ipfs/' + profile.image[0].contentUrl['/']
          "
        ></v-img>
      </v-avatar>
      <v-avatar size="40" v-if="!profile.image && address">
        <v-img :src="makeBlockie(address)"></v-img>
      </v-avatar>
    </v-col>
    <v-col cols="3">
      {{ profile.name || "" }} <br />
      {{ address && truncateAddr(address) }}
    </v-col>
  </v-row>
</template>

<script>
import { getProfile } from "3box/lib/api";
import mixins from "../utils/mixins";
export default {
  props: {
    address: String,
  },
  mixins: [mixins],
  data: () => ({
    profile: {},
  }),
  watch: {
    address: {
      handler: function(newVal) {
        getProfile(newVal)
          .then((data) => {
            this.profile = data;
          })
          .catch(() => {
            this.profile = {};
          });
      },
      immediate: true,
    },
  },
};
</script>
