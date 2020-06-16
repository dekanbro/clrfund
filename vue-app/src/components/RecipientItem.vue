<template>
  <v-row>
    <v-list-item-avatar>
      <v-img :src="item.avatar"></v-img>
    </v-list-item-avatar>

    <v-list-item-content>
      <v-col cols=2>
        <v-list-item-title v-text="item.title"></v-list-item-title>
        <v-list-item-subtitle v-text="item.address"></v-list-item-subtitle>
      </v-col>
      <v-col cols=10>
      <v-slider v-model="slider" class="align-center" color="pink" track-color="pink lighten-4" hide-details>
        <template v-slot:append>
          <v-text-field
            v-model="slider"
            class="mt-0 pt-0"
            hide-details
            single-line
            type="number"
            style="width: 60px"
          ></v-text-field>
        </template>
      </v-slider>
      </v-col>
    </v-list-item-content>

    <v-list-item-icon>
      <v-icon :color="item.active ? 'pink accent-4' : 'grey'"
        >mdi-arrow-up-down</v-icon
      >
    </v-list-item-icon>
    <v-list-item-icon>
      <v-icon :color="item.active ? 'pink accent-4' : 'grey'"
        >{{item.active ? "mdi-lock" : "mdi-lock-open"}}</v-icon
      >
    </v-list-item-icon>
  </v-row>
</template>

<script>
export default {
  props: {
    item: Object,
  },
  data: () => ({
    slider: 0,
  }),
};
</script>
