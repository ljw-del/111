<template>
  <div class="upload-container">
    <!-- 左侧区域 -->
    <div class="left-section">
      <h3>Finish!<br>Upload Your Resume</h3>
      <p>
        Upload your resume, the platform will help you parse and optimize, you
        can also skip this step
      </p>
      <img src="../assets/cat-illustration.png" alt="Cat Illustration" class="illustration" />
    </div>

    <!-- 右侧区域 -->
    <div class="right-section">
      <h2>Upload file</h2>
      <div
        class="upload-area"
        @click="openFileSelector"
        @dragover.prevent
        @drop="handleDrop"
      >
        <div class="upload-icon">
          <!-- 云图标 -->
<div class="icon">
  <img src="../assets/1.png" alt="上传图片" width="58" height="39">
</div>
        </div>
        <p>
          Drag your resume file to this area, or click on the area to select
          the appropriate file to upload
        </p>
        <input
          type="file"
          ref="fileInput"
          class="file-input"
          @change="handleFileChange"
          accept=".pdf,.doc,.docx"
        />
      </div>
      <div class="button-group">
        <button class="btn btn-outline" @click="goToLastStep">Last step</button>
        <button class="btn btn-primary" @click="submitUpload">Finish</button>
      </div>
      <div class="progress-indicator">
        <div class="step" :class="{ completed: currentStep >= 1 }"></div>
        <div class="step" :class="{ completed: currentStep >= 2 }"></div>
        <div class="step" :class="{ current: currentStep === 3 }"></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const fileInput = ref(null);
const selectedFile = ref(null);

const currentStep = ref(3);

// 打开文件选择器
const openFileSelector = () => {
  fileInput.value.click();
};

// 处理文件选择
const handleFileChange = (event) => {
  const file = event.target.files[0];
  if (file) {
    selectedFile.value = file;
    console.log('Selected file:', file.name);
  }
};

// 处理拖放
const handleDrop = (event) => {
  event.preventDefault();
  const file = event.dataTransfer.files[0];
  if (file) {
    selectedFile.value = file;
    console.log('Dropped file:', file.name);
  }
};

// 上一步
const goToLastStep = () => {
  console.log('Go to last step');
};

// 完成上传
const submitUpload = () => {
  if (selectedFile.value) {
    console.log('Uploading file:', selectedFile.value.name);
    // 这里可以添加上传逻辑
  } else {
    console.log('No file selected');
  }
};
</script>

<style scoped>
.upload-container {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 40px;
  background-color: #F8FBF9;
  height: 1080px;
  width: 1920px; 
  box-sizing: border-box;
  position: relative;
  
}

.left-section {
  width: 860px;
  height: 1080px;
  position: absolute; 
  left: 0;
  top: 0; 
  
}

.left-section h3 {
   width: 450px; 
  height: 110px;
  top: 124px;
  left: 102px;
  display: block;
  font-size: 40px;
  font-weight: 400;
  color: #000;
  line-height: 55px;
  letter-spacing: 0;
  position: absolute;
  margin: 0; 
  text-align: left;
}

.left-section p {
  width: 696px;
  height: 70px;
  top: 254px;
  left: 102px;
  display: block;
  position: absolute;
  text-align: left; 
  font-size: 20px;
  color: #a5a5a5;
  font-weight: 400;
  list-style: 35px;
  letter-spacing: 0%;
}

.left-section img {
  width: 763px;
  height: 569px;
  position: absolute;
  top: 511px;
  left: 0;
}

.right-section {
  position: absolute;
  top: 103px;
  left: 875px;
  width: 943px;
  height: 922px;
  background-color: #fff;
  padding: 32px;
  border-radius: 16px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  box-sizing: border-box; 
}

.right-section h2 {
  position: absolute;
  width: 214px;
  height: 35px;
  top: 30px;
  left: 125px;
  font-size: 36px;
  font-weight: 500;
  color: #060326;
  line-height: 35px;
  letter-spacing: 8%;
  text-align: left;
  margin: 0; 
  
}

.upload-area {
  position: absolute;
  width: 685px;
  height: 420px;
  top: 118px;
  left: 125px;
  border: 1px dashed #0538BB;
  background-color: #F2FAFF;
  border-radius: 8px;
  padding: 15px;
  margin: 0 auto 24px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  box-sizing: border-box; 
}
.upload-icon {
  width: 58px;
  height: 39px;
  top: 381px;
  left: 375px;
}

.upload-area p {
  width: 499px;
  height: 64px;
  top: 434px;
  left: 1097px;
  font-size: 16px;
  font-weight: 400;
  line-height: 32px;
  letter-spacing: 0%;
  color: #a5a5a5;
}

.file-input {
  display: none;
}

.button-group {
  display: flex;
  justify-content: center;
  margin-bottom: 24px;
}

.btn {
  padding: 12px 24px;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s ease;
}

.btn-outline {
  position: absolute;
  width: 272px;
  height: 67px;
  top: 621px;
  left: 200px;
  border-radius: 8px;
  background-color: #75ACFF;
  font-size: 24px;
  font-weight: 400;
  line-height: 35px;
  letter-spacing: 8%;
  color: #FFF;
}

.btn-primary {
  position: absolute;
  width: 272px;
  height: 67px;
  top: 621px;
  left: 500px;
  border-radius: 8px;
  background-color: #1B5AFF;
  font-size: 24px;
  font-weight: 400;
  line-height: 35px;
  letter-spacing: 8%;
  color: #fff;
}

.progress-indicator {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: absolute;
  bottom: 40px;
  left: 50%;
  transform: translateX(-50%);
  width: 200px; 
}

.step{
  width: 26px;
  height: 26px;
  border-radius: 50%;
  background-color: #85A7FF;
}

.step.current {
  background-color: #3b82f6;
}

.progress-indicator::before {
  content: '';
  position: absolute;
  top: 50%;
  left: -20px; 
  right: -20px; 
  height: 2px;
  background-color: #85A7FF;
  z-index: -1; 
}
</style>