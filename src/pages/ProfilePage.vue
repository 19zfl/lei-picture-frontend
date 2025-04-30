<template>
  <div class="gh-profile-root">
    <div class="gh-profile-main">
      <!-- 左侧栏 -->
      <aside class="gh-profile-sidebar">
        <div class="gh-profile-avatar-wrap">
          <a-image
            v-model:src="userParams.userAvatar"
            class="gh-profile-avatar"
            alt="头像"
          />
        </div>
        <h2 class="gh-profile-username">{{userParams.userName}}</h2>
        <div class="gh-profile-bio">{{userParams.userProfile}}</div>
        <div class="gh-profile-btns">
          <a-button type="primary">编辑资料</a-button>
        </div>
      </aside>
      <!-- 右侧内容 -->
      <section class="gh-profile-content">
        <div class="gh-profile-card">
          <h3 class="gh-profile-card-title">基本信息</h3>
          <div class="gh-profile-info-row">
            <span class="gh-profile-info-label">头像直链</span>
            <a-input
              v-model:value="userParams.userAvatar"
              class="gh-profile-input"
            />
          </div>
          <div class="gh-profile-info-row">
            <span class="gh-profile-info-label">用户名</span>
            <a-input v-model:value="userParams.userName" class="gh-profile-input" />
          </div>
          <div class="gh-profile-info-row">
            <span class="gh-profile-info-label">简介</span>
            <a-textarea
              v-model:value="userParams.userProfile"
              class="gh-profile-input"
              :auto-size="{ minRows: 2, maxRows: 4 }"
            />
          </div>
        </div>
        <div class="gh-profile-card" style="margin-top: 24px">
          <h3 class="gh-profile-card-title">其他信息</h3>
          <div class="gh-profile-info-row">
            <span class="gh-profile-info-label">角色</span>
            <span class="gh-profile-info-value">普通用户</span>
          </div>
          <!-- 可继续添加更多信息 -->
        </div>
      </section>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { useLoginUserStore } from '@/stores/useLoginUserStore'
import { onMounted, ref } from 'vue'

const loginUserStore = useLoginUserStore()

const userParams = ref({
  id: '',
  userAvatar: '',
  userName: '',
  userAccount: '',
  userProfile: '',
  userRole: '',
})

onMounted(() => {
  userParams.value = {...loginUserStore.loginUser}
  console.log(userParams.value)
})
</script>

<style>
.gh-profile-root {
  min-height: 100vh;
  padding: 32px 0;
}

.gh-profile-main {
  display: flex;
  max-width: 900px;
  margin: 0 auto;
  gap: 40px;
  align-items: flex-start;
}

.gh-profile-sidebar {
  width: 260px;
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 1.5px 8px rgba(140, 149, 159, 0.08);
  padding: 32px 24px 24px 24px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.gh-profile-avatar-wrap {
  width: 180px;
  height: 180px;
  border-radius: 50%;
  overflow: hidden;
  margin-bottom: 18px;
  border: 1.5px solid #eaecef;
  box-shadow: 0 2px 8px rgba(140, 149, 159, 0.1);
}

.gh-profile-avatar {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  background: #f5f5f5;
}

.gh-profile-username {
  font-size: 26px;
  font-weight: 700;
  color: #24292f;
  margin: 0 0 10px 0;
  text-align: center;
  word-break: break-all;
}

.gh-profile-bio {
  font-size: 15px;
  color: #57606a;
  margin-bottom: 18px;
  text-align: center;
  line-height: 1.6;
  word-break: break-all;
}

.gh-profile-btns {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 100%;
}

.gh-profile-content {
  flex: 1;
  min-width: 0;
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.gh-profile-card {
  background: #fff;
  border-radius: 8px;
  box-shadow: 0 1.5px 8px rgba(140, 149, 159, 0.08);
  padding: 28px 32px 24px 32px;
}

.gh-profile-card-title {
  font-size: 20px;
  font-weight: 600;
  color: #24292f;
  margin-bottom: 18px;
  letter-spacing: 1px;
}

.gh-profile-info-row {
  display: flex;
  align-items: flex-start;
  gap: 18px;
  margin-bottom: 18px;
}

.gh-profile-info-label {
  width: 80px;
  color: #57606a;
  font-size: 15px;
  font-weight: 500;
  flex-shrink: 0;
  line-height: 36px;
}

.gh-profile-info-value {
  color: #24292f;
  font-size: 15px;
  line-height: 36px;
}

.gh-profile-input {
  flex: 1;
  min-width: 0;
  border-radius: 6px;
  font-size: 15px;
  background: #f6f8fa;
  border: 1.5px solid #eaecef;
  padding: 8px 12px;
  transition:
    border 0.2s,
    box-shadow 0.2s;
  box-shadow: 0 1px 2px rgba(140, 149, 159, 0.03);
}

.gh-profile-input:focus {
  border: 1.5px solid #2da44e;
  background: #fff;
  box-shadow: 0 2px 8px rgba(64, 158, 255, 0.08);
}

/* 响应式 */
@media (max-width: 1000px) {
  .gh-profile-main {
    flex-direction: column;
    gap: 24px;
    align-items: stretch;
  }

  .gh-profile-sidebar {
    width: 100%;
    flex-direction: row;
    align-items: flex-start;
    gap: 24px;
    padding: 24px 16px;
  }

  .gh-profile-avatar-wrap {
    width: 120px;
    height: 120px;
    margin-bottom: 0;
    margin-right: 18px;
  }

  .gh-profile-username,
  .gh-profile-bio,
  .gh-profile-btns {
    text-align: left;
    align-items: flex-start;
  }
}

@media (max-width: 700px) {
  .gh-profile-main {
    padding: 0 8px;
  }

  .gh-profile-card {
    padding: 18px 8px 14px 8px;
  }
}
</style>
