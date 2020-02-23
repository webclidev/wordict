<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12"></v-col>
      <v-col class="mb-4">
        <h1 class="display-1 font-weight-bold mb-3">
          Type a word and see the magic
        </h1>
        <p>
          <v-text-field v-model="text"></v-text-field>
          {{ answer }}
        </p>
        <div v-for="(emoji, index) in emojis" :key="index">
          <v-icon
            :size="300"
            :color="emoji.color"
            v-if="emoji.rating === rating"
          >
            {{ emoji.name }}
          </v-icon>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";
export default {
  name: "Wordict",
  data() {
    return {
      text: "",
      answer: "",
      rating: null,
      emojis: [
        {
          name: "mdi-thought-bubble-outline",
          color: "blue darken-2",
          rating: 0
        },
        {
          name: "mdi-emoticon-dead-outline",
          color: "red accent-4",
          rating: 1
        },
        {
          name: "mdi-emoticon-cry-outline",
          color: "red accent-3",
          rating: 2
        },
        {
          name: "mdi-emoticon-frown-outline",
          color: "red accent-2",
          rating: 3
        },
        {
          name: "mdi-emoticon-sad-outline",
          color: "red accent-1",
          rating: 4
        },
        {
          name: "mdi-emoticon-tongue-outline",
          color: "teal accent-4",
          rating: 5
        },
        {
          name: "mdi-emoticon-wink-outline",
          color: "teal accent-3",
          rating: 6
        },
        {
          name: "mdi-emoticon-excited-outline",
          color: "teal accent-2",
          rating: 7
        },
        {
          name: "mdi-emoticon-outline",
          color: "green darken-2",
          rating: 8
        },
        {
          name: "mdi-emoticon-happy-outline",
          color: "green darken-3",
          rating: 9
        },
        {
          name: "mdi-emoticon-kiss-outline",
          color: "green darken-4",
          rating: 10
        }
      ]
    };
  },
  watch: {
    text() {
      setTimeout(
        that => {
          that.getAnswer();
        },
        500,
        this
      );
    }
  },
  methods: {
    async getAnswer() {
      this.answer = "Thinking...";
      let res = await axios.post("/user", this.text);
      console.log(res);
    }
  }
};
</script>
