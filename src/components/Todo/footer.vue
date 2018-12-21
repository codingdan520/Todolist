<template>
  <div id="footer">
    <span>制作人：{{autor}}</span>
  </div>
</template>

<script>
export default {
  name: "Footer",
  data() {
    return {
      autor: "彭丹"
    };
  }
};
</script>

<style lang="stylus" scoped>
#footer {
  margin-top: 50px;
  text-align: center;
  color: #d20a0a;
  font-size: 20px;
  text-shadow: 0 1px 0 black;
}
</style>

