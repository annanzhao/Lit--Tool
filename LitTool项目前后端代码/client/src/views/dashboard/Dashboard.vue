<template>
  <div class="main-panel">
    <div class="menus">
      <!-- 用户面板 -->
      <div class="user-panel">
        <div class="user-item" @click="showSubsection('username')">
          <i class="fas fa-user" style="color: #3498db;"></i> 用户名: Rinpa
        </div>
        <div class="user-item" @click="showSubsection('credit limit')">
          <i class="fas fa-credit-card" style="color: #e74c3c;"></i> 额度: 0.9
        </div>
      </div>
      <!-- 功能选择 -->
      <div class="menu-item-container">
        <div class="user-item" @click="showSubsection('featureSelection')">
          <i class="fas fa-cogs" style="color: #2ecc71;"></i> 功能选择页
        </div>
      </div>
      <!-- Lit Cite 菜单 -->
      <div @click="toggleLitCite" class="menu-item">
        <i class="fas fa-book" style="color: #f39c12;"></i> Lit Cite
      </div>
      <div v-if="showLitCite" class="submenu">
        <div @click="showSubsection('litCiteIntroduction')">
          <i class="fas fa-info-circle" style="color: #3498db;"></i> 介绍
        </div>
        <div @click="showSubsection('uploadLiterature')">
          <i class="fas fa-upload" style="color: #e74c3c;"></i> 上传文献
        </div>
        <div @click="showSubsection('startCitation')">
          <i class="fas fa-play" style="color: #2ecc71;"></i> 开始引用
        </div>
      </div>

      <!-- 侧栏菜单项 - Introduction -->
      <!-- 介绍子菜单项 -->
<div @click="toggleIntroduction" class="menu-item">
  <i class="fas fa-info" style="color: #3498db;"></i> Introduction
</div>
<div v-if="showIntroduction" class="submenu">
  <div @click="showSubsection('direction')" style="color: #3498db;">
    <i class="fas fa-info-circle" style="color: #3498db;"></i> 介绍
  </div>
  <div @click="showSubsection('generate')" style="color: #e74c3c;">
    <i class="fas fa-magic"></i> 整体生成
  </div>
  <div @click="showSubsection('researchOverview')" style="color: #2ecc71;">
    <i class="fas fa-search"></i> 研究问题
  </div>
  <div @click="showSubsection('researchDesign')" style="color: #f39c12;">
    <i class="fas fa-pencil-ruler"></i> 研究设计
  </div>
  <div @click="showSubsection('researchFindings')" style="color: #9b59b6;">
    <i class="fas fa-lightbulb"></i> 研究发现
  </div>
  <div @click="showSubsection('chapterArrangement')" style="color: #3498db;">
    <i class="fas fa-th-list"></i> 章节安排
  </div>
  <div @click="showSubsection('transitionalBackground')" style="color: #e74c3c;">
    <i class="fas fa-arrow-right"></i> 过渡段-背景
  </div>
  <div @click="showSubsection('transitionalProject')" style="color: #2ecc71;">
    <i class="fas fa-cogs"></i> 过渡段-项目
  </div>
  <div @click="showSubsection('transitionalLiterature')" style="color: #f39c12;">
    <i class="fas fa-book"></i> 过渡段-文献
  </div>
  <div @click="showSubsection('marginalContribution')" style="color: #9b59b6;">
    <i class="fas fa-plus"></i> 边际贡献
  </div>
</div>

      <!-- 登出 -->
      <div class="user-item user-logout" @click="logout">
        <i class="fas fa-sign-out-alt" style="color: #e74c3c;"></i> 登出
      </div>
    </div>

    <div style="padding: 20px; width: 100%">
      <router-view></router-view>
    </div>
  </div>
</template>

  
  <script setup>
  import { AdminStore } from '../../stores/AdminStore'
  import { ref, inject } from 'vue'
  import { useRouter } from 'vue-router'
  const router = useRouter()
  
  const message = inject("message")
  const axios = inject("axios")
  
  const adminStore = AdminStore()
  
  const showIntroduction = ref(false);
  const showLitCite = ref(false);

  const toggleLitCite = () => {
    showLitCite.value = !showLitCite.value;
  };
  
  const toggleIntroduction = () => {
    showIntroduction.value = !showIntroduction.value;
  };
  
  const showSubsection = (section) => {
    console.log(`Clicked on ${section}`);
    if (section === 'researchOverview') {
      router.push("/dashboard/overview");
    } else if (section === 'IntroGenius') {
      router.push("/dashboard/IntroGenius");
    } else if (section === 'researchDesign') {
      router.push("/dashboard/design");
    } else if (section === 'researchFindings') {
      router.push("/dashboard/findings");
    } else if (section === 'chapterArrangement') {
      router.push("/dashboard/chapter");
    } else if (section === 'transitionalBackground') {
      router.push("/dashboard/Background");
    } else if (section === 'transitionalProject') {
      router.push("/dashboard/Project");
    } else if (section === 'transitionalLiterature') {
      router.push("/dashboard/Literature");
    } else if (section === 'marginalContribution') {
      router.push("/dashboard/Contribution");
    } else if (section === 'direction') {
      router.push("/dashboard/Direction");
    } else if (section === 'featureSelection') {
      router.push("/dashboard/Selection");
    } else if (section === 'generate') {
      router.push("/dashboard/Generate");
    }else if (section === 'uploadLiterature') {
      router.push("/dashboard/Upload");
    }else if (section === 'startCitation') {
      router.push("/dashboard/startCitation");
    }
  };
  
  // 路由跳转
  const toPage = (menu) => {
    if (menu.href === 'logout') {
      router.push("/login");
    } else {
      router.push(menu.href);
    }
  };
  
  const logout = () => {
    router.push("/login");
  };
  </script>
  
  <style lang="scss" scoped>
  @import "@fortawesome/fontawesome-free/css/all.min.css";

  .main-panel {
  display: flex;
  color: #64676a;
  max-width: 1500px;
  margin: 0 auto;
}

.menus {
  padding: 20px 0;
  box-sizing: border-box;
  text-align: center;
  width: 180px;
  height: 95vh;
  border-right: 1px solid #dadada;
}


.menu-item,
.submenu,
.user-logout {
  cursor: pointer;
  border: 1px solid #fd760e;
  padding: 10px;
  margin: 5px;
  border-radius: 5px;
  transition: background-color 0.3s, color 0.3s; /* 添加过渡效果 */
}


.submenu {
  margin-left: 10px;
  text-align: left;
}

/* 修改以下样式，使用透明度来调整颜色 */
.user-introduction,
.menu-item-container,
.lit-cite {
  cursor: pointer;
  border: 1px solid rgba(253, 118, 14, 0.8); /* 调整透明度 */
  padding: 10px;
  margin: 5px;
  border-radius: 5px;
  transition: background-color 0.3s, color 0.3s; /* 添加过渡效果 */
}



.title {
  font-size: 65px;
  font-weight: bold;
  text-align: right;
  position: fixed;
  color: rgba(0, 0, 0, 20%);
  right: calc((100vw - 1500px) / 2);
  bottom: 20px;
}
</style>