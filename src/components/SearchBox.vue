<template>
  <div class="search-container">
    <!-- 输入框 + 搜索按钮 -->
    <select v-model="selectedEngine">
      <option v-for="engine in engines" :key="engine.name" :value="engine">
        {{ engine.name }}
      </option>
    </select>
    <input type="text" v-model="searchQuery" placeholder="请输入搜索内容" @keyup.enter="search">
    <button @click="search">搜索</button>
  </div>
</template>

<script>
export default {
  name: 'SearchBox',
  data() {
    return {
      searchQuery: '',       // 绑定的搜索关键词
      selectedEngine: null,  // 当前选中的搜索引擎
      // 支持的搜索引擎列表
      engines: [
        {
          name: 'Bing',
          url: 'https://www.bing.com/search?q='
        },
        {
          name: '百度',
          url: 'https://www.baidu.com/s?wd='
        },
        {
          name: 'Google',
          url: 'https://www.google.com/search?q='
        }
      ]
    }
  },
  mounted() {
    // 默认选中第一个搜索引擎
    this.selectedEngine = this.engines[0]
  },
  methods: {
    search() {
      if (!this.searchQuery.trim()) {
        alert('搜索内容不能为空！')
        return
      }
      // 跳转到搜索引擎（编码关键词）
      const encodedQuery = encodeURIComponent(this.searchQuery)
      window.open(`${this.selectedEngine.url}${encodedQuery}`, '_blank')
    }
  }
}
</script>

<style scoped>
.search-container {
  display: flex;
  font-size: 16px;
  /* 默认基准（用户未缩放时） */
  justify-content: center;
  gap: 0px;
  margin-top: 0;
  width: 100%;
}

input {
  width: 55%;
  height: 32px;
  background-color: rgba(255, 255, 255, 0.3);
  backdrop-filter: blur(10px);
  /* 模糊背景 */
  border: none;
  outline: none;
  border-bottom: 2px solid #ccc;
  line-height: 1.5;
  /* 合适的行高 */
  padding: 0px 18px;
  /* 上下2px，左右18px */
  font-size: 18px;
}

select {
  width: 6%;
  min-width: 40px;
  max-width: max-content;
  border: none;
  padding: 0px;
  outline: none;
  border-radius: 15px 0 0 15px;
  background-color: rgba(255, 255, 255, 0.3);
  backdrop-filter: blur(10px);
  border-bottom: 2px solid #ccc;
  white-space: nowrap;
  /* 禁止文字换行 */
  overflow: hidden;
  appearance: none; /* 移除默认的下拉箭头 */
  font-size: clamp(5px, 1.5vw + 0.2rem, 16px);
}

button {
  width: 8%;
  min-width: 50px;
  max-width: 110px;
  height: 33px;
  border-radius: 0 15px 15px 0;
  background-color: rgba(34, 78, 239, 0.311);
  backdrop-filter: blur(10px);
  cursor: pointer;
  border: none;
  border-bottom: 2px solid #ccc;
  outline: none;
  white-space: nowrap;
  /* 禁止文字换行 */
  overflow: hidden;
  font-size: clamp(8px, 1.5vw + 0.5rem, 18px);
}

button:hover {
  background: rgba(34, 78, 239, 0.311);
}
</style>