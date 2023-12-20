<template>
    <div class="container container-left">
      <div class="title">研究问题模块</div>
  
      <div class="input-box">
        <label for="articleTitle" class="left-label">你文章的标题是什么?</label>
        <input v-model="articleTitle" type="text" id="articleTitle" placeholder="Example: Fighting violence against women: The role of female political representation" style="color: #888;">
      </div>
  
      <div class="input-box">
        <label for="coreStory" class="left-label">你文章的核心故事是什么? 你文章研究的是什么问题?</label>
        <textarea v-model="coreStory" id="coreStory" placeholder="Example: The effect of female political representation on domestic violence" style="color: #888;"></textarea>
      </div>
  
      <button @click="submitForm">Submit</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        articleTitle: "",
        coreStory: ""
      };
    },
    methods: {
      submitForm() {
        // 在这里可以进行提交操作，例如将数据发送到服务器
        // 这里只是简单地在控制台输出
        console.log('Article Title:', this.articleTitle);
        console.log('Core Story:', this.coreStory);
      }
    }
  };
  </script>
  
  <style scoped>
  .container {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  
  .container-left {
    margin-left: 20px; /* 调整左边距 */
  }
  
  .title {
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 20px;
  }
  
  .input-box {
    margin-bottom: 15px;
  }
  
  .left-label {
    text-align: left;
    display: block;
    margin-bottom: 5px;
  }
  
  input,
  textarea {
    width: 100%;
    padding: 10px;
    box-sizing: border-box;
    margin-top: 5px;
    border: 1px solid #ccc;
    border-radius: 5px;
    resize: vertical;
  }
  
  button {
    background-color: #4caf50;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  </style>  