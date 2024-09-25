<template>
    <el-contain class="home">
        <!-- <el-header height="160px"> -->
            <div class="timeDiv">
                <span class="time">{{ currentTime }}</span>
            </div>
    

    <div class="shell">
        <div class="content">
            <div class="item"></div>
            <div class="item"></div>
            <div class="item"></div>
        </div>
    </div>
<!-- </el-main> -->
    </el-contain>
  </template>
  <script setup lang="ts">

    import { ref } from 'vue'


    const currentTime = ref('');

const updateTime = () => {
  const now = new Date();
  const hours = now.getHours().toString().padStart(2, '0');
  const minutes = now.getMinutes().toString().padStart(2, '0');
  const seconds = now.getSeconds().toString().padStart(2, '0');

  const pastDate = new Date('Sep 17, 2024 9:00:00'); // Replace with your specific date and time

// Calculate the difference in milliseconds
const difference = now.getTime() - pastDate.getTime();

// Convert the difference in milliseconds to hours, minutes, and seconds
const diffHours = Math.floor(difference / 3600000); // 3600000 milliseconds in an hour
const day = Math.floor(diffHours / 24);
const hour = diffHours % 24
const diffMinutes = Math.floor((difference % 3600000) / 60000); // 60000 milliseconds in a minute
const diffSeconds = Math.floor((difference % 60000) / 1000); // 1000 milliseconds in a second
currentTime.value = '豪 ♥ ♥ 霞 '+' '+ `${day}天${hour}时${diffMinutes}分${diffSeconds}秒`;
};

const intervalId = setInterval(updateTime, 1000);

updateTime();

</script>
<style>


  .timeDiv{
       text-align: center;
       margin: 80px 0px 30px 0px;
  }
  .time{
        font-size: 45px;
        color: #f14b4b8e;
  } 

  .home{
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    height: 90vh; 
    overflow: hidden;
  }

body {
  background-image: linear-gradient(to top, #eddae33c 0%, #eac7d7c1 100%);

}
/* 定义外层容器样式 */
.shell {
    position: relative;
    /* 相对定位 */
    width: 60vw;
    /* 宽度占视口宽度的60% */
    height: 60vw;
    /* 高度占视口高度的40% */
    max-width: 380px;
    /* 最大宽度为380像素 */
    max-height: 500px;
    /* 最大高度为250像素 */
    margin: 0;
    /* 外边距为0 */
    color: white;
    /* 字体颜色为白色 */
    perspective: 1000px;
    /* 透视效果，观察者与z=0平面的距离 */
    transform-origin: center;
    /* 变形原点为中心 */
    
}

/* 定义内容容器样式 */
.content {
    display: flex;
    /* 设置为弹性盒子布局 */
    justify-content: center;
    /* 主轴居中对齐 */
    align-items: center;
    /* 交叉轴居中对齐 */
    position: absolute;
    /* 绝对定位 */
    width: 100%;
    /* 宽度100% */
    height: 100%;
    /* 高度100% */
    transform-origin: center;
    /* 变形原点为中心 */
    transform-style: preserve-3d;
    /* 保持3D变换 */
    transform: translateZ(-30vw) rotateY(0);
    /* 变换：沿z轴平移-30vw，绕y轴旋转0度 */
    animation: carousel 9s infinite cubic-bezier(0.77, 0, 0.175, 1) forwards;
    /* 动画：名称为carousel，持续时间9秒，无限循环，缓动函数为cubic-bezier(0.77, 0, 0.175, 1)，动画结束后保持最后状态 */
}

/* 定义项目样式 */
.item {
    position: absolute;
    /* 绝对定位 */
    width: 60vw;
    /* 宽度占视口宽度的60% */
    height: 40vw;
    /* 高度占视口高度的40% */
    max-width: 260px;
    /* 最大宽度为380像素 */
    max-height: 460px;
    /* 最大高度为250像素 */
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
    /* 设置阴影 */
    border-radius: 6px;
    /* 边框圆角半径为6像素 */
    background-size: cover;
    /* 背景图片等比例缩放并覆盖整个容器 */
    -webkit-box-reflect: below 25px -webkit-linear-gradient(transparent 50%, rgba(255, 255, 255, 0.3));
    /* 创建倒影效果 */
}

/* 第一个项目样式 */
.item:nth-child(1) {
    background-image: url(../assets/1.jpg);
    /* 背景图片为01.jpg */
    transform: rotateY(0) translateZ(35vw);
    /* 变换：绕y轴旋转0度，沿z轴平移35vw */
}

/* 第二个项目样式 */
.item:nth-child(2) {
    background-image: url(../assets/2.jpg);
    /* 背景图片为02.jpg */
    transform: rotateY(120deg) translateZ(35vw);
    /* 变换：绕y轴旋转120度，沿z轴平移35vw */
}

/* 第三个项目样式 */
.item:nth-child(3) {
    background-image: url(../assets/3.jpg);
    /* 背景图片为03.jpg */
    transform: rotateY(240deg) translateZ(35vw);
    /* 变换：绕y轴旋转240度，沿z轴平移35vw */
}

/* 定义动画 */
@keyframes carousel {

    0%,
    17.5% {
        transform: translateZ(-35vw) rotateY(0);
        /* 变换：沿z轴平移-35vw，绕y轴旋转0度 */
    }

    27.5%,
    45% {
        transform: translateZ(-35vw) rotateY(-120deg);
        /* 变换：沿z轴平移-35vw，绕y轴旋转-120度 */
    }

    55%,
    72.5% {
        transform: translateZ(-35vw) rotateY(-240deg);
        /* 变换：沿z轴平移-35vw，绕y轴旋转-240度 */
    }

    82.5%,
    100% {
        transform: translateZ(-35vw) rotateY(-360deg);
        /* 变换：沿z轴平移-35vw，绕y轴旋转-360度 */
    }
}
@media (max-width: 768px) {
    .home{
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    height: 77vh; 
    overflow: hidden;
  }

  .timeDiv{
       text-align: center;
       margin: 0px 0px 80px 0px;
  }
  .time{
        font-size: 25px;
        color: #f14b4b8e;
  } 
  .item {
    position: absolute;
    /* 绝对定位 */
    width: 39vw;
    /* 宽度占视口宽度的60% */
    height: 75vw;
    /* 高度占视口高度的40% */
    max-width: 260px;
    /* 最大宽度为380像素 */
    max-height: 450px;
    /* 最大高度为250像素 */
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.3);
    /* 设置阴影 */
    border-radius: 6px;
    /* 边框圆角半径为6像素 */
    background-size: cover;
    /* 背景图片等比例缩放并覆盖整个容器 */
    -webkit-box-reflect: below 25px -webkit-linear-gradient(transparent 50%, rgba(255, 255, 255, 0.3));
    /* 创建倒影效果 */
}
}
</style>