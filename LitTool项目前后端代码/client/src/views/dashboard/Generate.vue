<template>
  <div class="container container-left">
    <div class="title">整体生成</div>

    <div class="input-box">
      <label for="articleTitle" class="left-label">你文章的标题是什么?</label>
      <input v-model="articleTitle" type="text" id="articleTitle" placeholder="Example: Fighting violence against women: The role of female political representation" class="custom-input">
    </div>

    <div class="input-box">
      <label for="coreStory" class="left-label">核心故事或研究问题</label>
      <textarea v-model="coreStory" id="coreStory" placeholder="Example: The effect of female political representation on domestic violence" class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="empiricalStrategy" class="left-label">实证策略</label>
      <textarea v-model="empiricalStrategy" id="empiricalStrategy" placeholder="Example: regression discontinuity (RD)" class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="mainIdeas" class="left-label">实证策略的主要思路</label>
      <textarea v-model="mainIdeas" id="mainIdeas" placeholder="Example: We compare Brazilian municipalities where a female candidate barely won..." class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="datasetIntroduction" class="left-label">数据集介绍</label>
      <textarea v-model="datasetIntroduction" id="datasetIntroduction" placeholder="Example: BVamp eHomicde and iolence ata source..." class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="researchFinding1" class="left-label">研究发现1</label>
      <textarea v-model="researchFinding1" id="researchFinding1" placeholder="Example: we find that the presence of a female mayor leads to a 50%..." class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="researchFinding2" class="left-label">研究发现2</label>
      <textarea v-model="researchFinding2" id="researchFinding2" placeholder="Example: These results are not attributable to pre-existing municipal characteristics..." class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="researchFinding3" class="left-label">研究发现3</label>
      <textarea v-model="researchFinding3" id="researchFinding3" placeholder="Example: Collectively, our findings offer compelling evidence that women in office play a significant role..." class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="articleStructure" class="left-label">文章结构</label>
      <textarea v-model="articleStructure" id="articleStructure" placeholder="Example: 2. Institutional background; 3. Data; 4. Empirical strategy; 5. Results; 6. Potential mechanisms; 7. Conclusion" class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="background" class="left-label">背景</label>
      <textarea v-model="background" id="background" placeholder="Example: The background and prevalence of violence against women" class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="backgroundInformation" class="left-label">Background Information</label>
      <textarea v-model="backgroundInformation" id="backgroundInformation" placeholder="Example: The background and prevalence of violence against women, highlighting the global significance..." class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="projectIntroduction" class="left-label">项目介绍</label>
      <textarea v-model="projectIntroduction" id="projectIntroduction" placeholder="Example: APRP (Area Poverty Reduction Program)" class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="projectDetails" class="left-label">项目的详细信息</label>
      <textarea v-model="projectDetails" id="projectDetails" placeholder="Example: Cammmt cae o es m m t sMilaest rearby tons..." class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="relatedLiterature" class="left-label">相关文献</label>
      <textarea v-model="relatedLiterature" id="relatedLiterature" placeholder="Example: (1) Hessami.Z.. da Fonseca ML.. 2020.Female political representation and su..." class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="abstract" class="left-label">摘要</label>
      <textarea v-model="abstract" id="abstract" placeholder="Example: Famo ele muesieate te erecto womens o a eadersto m oa oemert o omesicyo ente aanst women..." class="custom-textarea"></textarea>
    </div>

    <div class="input-box">
      <label for="relatedLiteratureTitle" class="left-label">相关文献标题与简介</label>
      <textarea v-model="relatedLiteratureTitle" id="relatedLiteratureTitle" placeholder="Example: 1. Decarolis, F., Fisman, R., Pinotti, P., Vannutelli, S., Wang, Y., 202. Gender and bureaucratic corruption: Evidence from two countries. J. Law Econ." class="custom-textarea"></textarea>
    </div>

    <button @click="submitForm">Submit</button>
  </div>
</template>

<script>
export default {
  methods: {
    submitForm() {
      console.log('文章标题:', this.articleTitle);
      console.log('核心故事或研究问题:', this.coreStory);
      console.log('实证策略:', this.empiricalStrategy);
      console.log('实证策略的主要思路:', this.mainIdeas);
      console.log('数据集介绍:', this.datasetIntroduction);
      console.log('研究发现1:', this.researchFinding1);
      console.log('研究发现2:', this.researchFinding2);
      console.log('研究发现3:', this.researchFinding3);
      console.log('文章结构:', this.articleStructure);
      console.log('背景:', this.background);
      console.log('Background Information:', this.backgroundInformation);
      console.log('项目介绍:', this.projectIntroduction);
      console.log('项目的详细信息:', this.projectDetails);
      console.log('相关文献:', this.relatedLiterature);
      console.log('摘要:', this.abstract);
      console.log('相关文献标题与简介:', this.relatedLiteratureTitle);
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
  margin-left: 20px;
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

.custom-input,
.custom-textarea {
  width: 100%;
  padding: 10px;
  box-sizing: border-box;
  margin-top: 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
  resize: vertical;
  font-size: 16px;
  color: #888; /* 灰色文本颜色 */
}

button {
  background-color: #4caf50;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}
</style>
