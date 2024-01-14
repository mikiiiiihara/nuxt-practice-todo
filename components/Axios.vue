<template>
  <div>
    <h1>データ一覧</h1>
    <ul>
      <li v-for="item in items" :key="item.id">{{ item.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [],
    };
  },
  async mounted() {
    try {
      const response = await this.$axios.get(
        "https://developer.am.mufg.jp/fund_information_all_latest/"
      );
      response.data.datasets.map((value) =>
        this.items.push({ id: value.fund_cd, name: value.fund_name })
      );
    } catch (error) {
      console.error("APIからデータを取得できませんでした:", error);
    }
  },
};
</script>
