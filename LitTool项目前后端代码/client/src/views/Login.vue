<template>
    <div class="login-panel">
        <h2 class="n-title">
        <i class="fas fa-smile" style="color: #e74c3c;"></i> Welcome to Login
      </h2>
        <n-card title="LitTool用户登录">
            <n-form :rules="rules" :model="admin">
                <n-form-item path="account" label="账号">
                    <i class="fa fa-user"></i> <!-- 账号图标 -->
                    <n-input v-model:value="admin.account" placeholder="请输入账号" />
                </n-form-item>
                <n-form-item path="password" label="密码">
                    <i class="fa fa-lock"></i> <!-- 密码图标 -->
                    <n-input v-model:value="admin.password" type="password" placeholder="请输入密码" />
                </n-form-item>
            </n-form>
            <template #footer>
                <n-checkbox v-model:checked="admin.rember" label="记住我" />
                <n-button @click="login">登录</n-button>
            </template>
        </n-card>
    </div>
</template>

<script setup>
import { ref, reactive, inject } from 'vue'
import { AdminStore } from '../stores/AdminStore'
import { useRouter } from 'vue-router'

const router = useRouter()
const message = inject("message")
const axios = inject("axios")
const adminStore = AdminStore()

// 验证表单规则
let rules = {
    account: [
        { required: true, message: "请输入账号", trigger: "blur" },
        { min: 3, max: 12, message: "账号长度在 3 到 12 个字符", trigger: "blur" },
    ],
    password: [
        { required: true, message: "请输入密码", trigger: "blur" },
        { min: 6, max: 18, message: "密码长度在 6 到 18 个字符", trigger: "blur" },
    ],
};

// 管理员登录数据
const admin = reactive({
    account: localStorage.getItem("account") || "",
    password: localStorage.getItem("password") || "",
    rember: localStorage.getItem("rember") == 1 || false
})

// 登录
const login = async () => {
    let result = await axios.post("/admin/login", admin);
    if (result.data.code == 200) {
        // 处理登录成功逻辑
        router.push("/dashboard/selection")
        message.info("登录成功")
    } else {
        message.error("登录失败")
    }
}
</script>

<style lang="scss" scoped>
  @import "@fortawesome/fontawesome-free/css/all.min.css";
  .login-panel {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    color: #fff;
    background: linear-gradient(to right, #ecf0f1, #c8dfee);
    text-align: center;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .n-card {
  width: 500px;
  padding: 20px;
  box-sizing: border-box;
  background: linear-gradient(to right, #ecf0f1, #c8dfee);
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.147);
}


  .n-title {
    margin-bottom: 20px;
    font-size:35px;
  }

  .n-button {
    width: 100%;
    margin-top: 10px;
  }

  .fa {
    margin-right: 10px;
    color: #158bdb;
  }

  .n-input {
    transition: all 0.3s ease;
    &:hover {
      transform: scale(1.05);
    }
  }

  .n-form-item {
    margin-bottom: 15px;
  }
</style>