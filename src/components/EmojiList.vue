<template>
  <div class="emoji-list">
    <div
      class="emoji-item"
      v-for="(emojiItem, index) in emojiList"
      :key="index"
    >
      <p class="emoji-icon">{{ emojiItem.symbol }}</p>
      <p class="emoji-title">{{ emojiItem.title }}</p>
      <p class="emoji-keywords">{{ emojiItem.keywords }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    emojiList: {
      required: true,
    },
  },

  name: "EmojiList",
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

p {
  color: black;
}

.emoji-icon {
  font-weight: 400;
  font-size: 48px;
  margin-top: 30px;
}

.emoji-title {
  font-weight: 700;
  font-size: 17px;
  margin-top: 18px;
  line-height: 28px;

  text-decoration-line: underline;
}

.emoji-keywords {
  margin-top: 12px;
  font-weight: 400;
  font-size: 12px;
  line-height: 15px;
  text-align: center;

  color: #3f444a;
}

.emoji-item {
  width: 316px;
  height: 185px;

  margin-bottom: 25px;

  border: 1px solid #dee2e6;
  border-radius: 4px;
  box-shadow: 0 8px 35px rgba(0, 0, 0, 0.15);
  transition: 0.3s;
}

.emoji-item:hover {
  box-shadow: 0 8px 35px rgba(0, 0, 0, 0.25);
}

.emoji-list {
  margin: 68px auto 0;
  display: flex;
  flex-wrap: wrap;
  width: 1000px;
  justify-content: space-between;
  flex-direction: row;
}
</style>
