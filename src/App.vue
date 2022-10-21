<template>
  <header>
    <h1><img src="./assets/logo.png" alt="" />Emoji Finder</h1>
    <p>Find emoji by keywords {{}}</p>
    <input
      type="search"
      name="emoji-search-bar"
      id="emoji-search-bar"
      class="emoji-search-bar"
      placeholder="Type in emoji..."
      v-model="searchQuery"
    />
  </header>
  <emoji-list :emoji-list="filteredEmojis"></emoji-list>
</template>

<script>
import EmojiList from "@/components/EmojiList";

async function fetchEmojis(path) {
  const request = new Request(path);
  const response = await fetch(request);

  return response.json();
}

export default {
  data() {
    return {
      itemsList: null,
      searchQuery: "",
    };
  },
  name: "App",
  components: {
    EmojiList,
  },
  computed: {
    filteredEmojis() {
      if (!this.searchQuery) {
        return this.itemsList;
      } else {
        return this.itemsList.filter(({ keywords }) =>
          keywords.includes(this.searchQuery.toLowerCase())
        );
      }
    },
  },
  mounted() {
    fetchEmojis("https://emoji-api-app.herokuapp.com/").then(
      (emo) => (this.itemsList = emo)
    );
  },
};
</script>

<style>
#app {
  font-family: Inter, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;

  color: #2c3e50;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

header {
  background: linear-gradient(92.33deg, #196b78 0.12%, #138496 100%);
  padding-top: 64px;
  box-shadow: 0 8px 35px rgba(0, 0, 0, 0.16);
}

h1 {
  display: flex;
  align-items: center;
  justify-content: center;

  font-weight: 700;
  font-size: 72px;

  color: #ccf8ff;
}

p {
  font-weight: 400;
  font-size: 21px;
  line-height: 36px;
  margin: 12px 0;
  padding-bottom: 64px;

  color: rgba(204, 248, 255, 0.75);
}

img {
  width: 40px;
  opacity: 0.8;
  margin-right: 10px;
}

.emoji-search-bar {
  border: 1px solid #ced4da;
  height: 64px;
  width: 820px;
  border-radius: 4px;

  font-size: 24px;
  color: #abb5be;
  padding-left: 32px;
  margin-bottom: -20px;
}
</style>
