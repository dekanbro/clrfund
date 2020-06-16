<template>
  <v-container>
    <v-row>
      <v-col cols=1>
        <v-avatar size="40">
          <v-img src="https://cdn.vuetifyjs.com/images/lists/5.jpg"></v-img>
        </v-avatar>
      </v-col>
      <v-col cols=2>
        some text <br />
        some other text
      </v-col>
      <v-col cols=7>
        <span>100 DAI</span>
        <v-progress-linear v-model="fundsAllocated" height="25" color="pink" track-color="pink lighten-4">
          <template v-slot="{ value }">
            <strong>{{ Math.ceil(value) }}%</strong>
          </template>
        </v-progress-linear>
      </v-col>
      <v-col>
        <v-btn text color="pink accent-4">Fund</v-btn>
      </v-col>
    </v-row>
    <v-list subheader>
      <v-divider></v-divider>
      <v-list-item
        v-for="item in items"
        :key="item.title"
        @click="selectRecipient(item)"
      >
        <RecipientItem :item="item"></RecipientItem>
      </v-list-item>
    </v-list>

  </v-container>
</template>

<script>
import RecipientItem from "../components/RecipientItem";

export default {
  data: () => ({
    fundsAllocated: 20,
    max: 100,
    min: 0,
    items: [
      {
        active: true,
        title: "Jason Oner",
        address: "0x1234....56789",
        avatar: "https://i.imgur.com/hnhW457.png",
        description: "Aenean sollicitudin, lorem quis bibendum auctor, nisi elit consequat ipsum, nec sagittis. Duis sed odio sit amet nibh vulputate cursus a sit amet mauris. Morbi accumsan ipsum velit. Nam nec tellus a odio tincidunt auctor a ornare odio."
      },
      {
        active: true,
        title: "Ranee Carlson",
        address: "0x1234....56789",
        avatar: "https://i.imgur.com/iwg5Aic.png",
        description: "Lorem Ipsum proin gravida nibh vel velit auctor aliquet. Aenean sollicitudin, lorem quis bibendum auctor, nisi elit consequat ipsum, nec sagittis. Duis sed odio sit amet nibh vulputate cursus a sit amet mauris. Morbi accumsan ipsum velit. Nam nec tellus a odio tincidunt auctor a ornare odio."
      },
      {
        title: "Cindy Baker",
        address: "0x1234....56789",
        avatar: "https://i.imgur.com/U7IAdQa.png",
        description: "Morbi accumsan ipsum velit. Nam nec tellus a odio tincidunt auctor a ornare odio. Lorem Ipsum proin gravida nibh vel velit auctor aliquet. Aenean sollicitudin, lorem quis bibendum auctor, nisi elit consequat ipsum, nec sagittis. Duis sed odio sit amet nibh vulputate cursus a sit amet mauris."
      },
      {
        title: "Ali Connors",
        address: "0x1234....56789",
        avatar: "https://i.imgur.com/R4TZsxC.png",
        description: "Ipsum proin gravida nibh vel velit auctor aliquet. Aenean sollicitudin, lorem quis bibendum auctor, nisi elit consequat ipsum, nec sagittis. Duis sed odio sit amet nibh vulputate cursus a sit amet mauris. Morbi accumsan ipsum velit. Nam nec tellus a odio tincidunt auctor a ornare odio."
      },
    ],
  }),
  components: { RecipientItem },
  methods: {
    selectRecipient(recipient) {
      console.log("recipient", recipient);
      this.$emit("selectRecipient", recipient);
    },
  },
};
</script>
