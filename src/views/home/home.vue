<template>
  <div class="container" :class="{'on-active-body-2': activePage == 2, 'on-active-body-3': activePage == 3}">
    <div id="homePage" v-show="activePageDelay == 1">
      <div class="head-box">
        <div class="logo-box"></div>
        <div class="header">
          <ul>
            <li @click="switchPage(2)">关于我们</li>
            <li @click="switchPage(3)">意见反馈</li>
            <li>
  <el-popover
    ref="popover"
    placement="bottom"
    width="50"
    trigger="hover"
    >
    <img src="../../assets/wx_concat.jpg" alt="" width="30px" height="0px">
  </el-popover>
  <span v-popover:popover>小程序</span>
            <li
              class="pro-hover"
              @mouseenter="onProHover"
              @mouseleave="isHover = false"
            >{{isHover ? '年付用户额外获得一年' : '升级PRO'}}</li>
            <li>
              <div class="switch-btn" @click="isSwitch = !isSwitch">
                <div>CN</div>
                <div>EN</div>
                <div
                  class="switch-circle"
                  :class="{'slide-left': isSwitch, 'slide-right': !isSwitch}"
                ></div>
              </div>
            </li>
          </ul>
        </div>
      </div>
      <div class="body">
        <div class="content">
          <!-- <div>
          <span>Runni…me.7z</span>
          <span>- 110.0 MB</span>
        </div>
        <div></div>
        <div></div>
          <div></div>-->
          <div
            class="upoload-btn"
            :class="{'slide-left': activeCircle == 1, 'slide-right': activeCircle == 2}"
          >
            <div style="position: relative;">
              <div
                class="left-circle"
                @mouseenter="activeCircle = 1"
                @mouseleave="activeCircle = 0"
              >
                <div class="add-file">添加文件</div>
              </div>
              <div
                class="right-circle"
                @mouseenter="activeCircle = 2"
                @mouseleave="activeCircle = 0"
              >
                <span class="login-btn">登陆</span>
              </div>
            </div>
          </div>
        </div>
        <div class="picture-box">
          <div class="img-box">
            <div class="zoom-btn" @mouseover="zoomHover = true" @mouseleave="zoomHover = false">
              <div class="dashed-square">
                <div class="solid-square"></div>
              </div>
            </div>
            <img
              class="img-top"
              src="https://background.cowtransfer.com/1545730330131Discount Kickerclub 02.jpg?imageView2/0/format/jpg/interlace/1/q/60|imageslim"
              alt
            >
            <img
              class="img-bottom"
              :class="{'img-bottom-zoom': zoomHover}"
              src="https://background.cowtransfer.com/1545730330131Discount Kickerclub 02.jpg?imageView2/0/format/jpg/interlace/1/q/60|imageslim"
              alt
            >
          </div>
        </div>
      </div>
      <div class="footer">
        <p>服务协议©2018-2019 成都氪林斯软件有限公司版权所有。ICP: 蜀ICP备14008877号-3</p>
      </div>
    </div>
    <div id="secondPage" v-if="activePage == 2" :class="{'on-active': activePage == 2}">
      <div class="close-btn" @click="activePageDelay = 1;activePage = 1;">
        <span><span style="font-size: 20px;">✘</span>关闭</span>
      </div>
      <h1 class="waiting">待定...</h1>
    </div>
    <div id="secondPage" v-if="activePage == 3" :class="{'on-active': activePage == 3}">
      <div class="close-btn" @click="activePageDelay = 1;activePage = 1;">
        <span><span style="font-size: 20px;">✘</span>关闭</span>
      </div>
      <h1 class="waiting">待定...</h1>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isHover: false,
      zoomHover: false,
      activeCircle: 0,
      isSwitch: false,
      activePageDelay: 1,
      activePage: 1,
      imgArr: [
        {
          name: "tupianyi",
          url:
            "https://background.cowtransfer.com/1545730330131Discount Kickerclub 02.jpg?imageView2/0/format/jpg/interlace/1/q/60|imageslim"
        },
        {
          name: "tupianer",
          url:
            "https://background.cowtransfer.com/wallpaper/static/1557111940263/Aslan 007.jpg?imageView2/0/format/jpg/interlace/1/q/60|imageslim"
        }
      ]
    };
  },
  methods: {
    onProHover() {
      setTimeout(() => {
        this.isHover = true;
      }, 100);
    },
    switchPage(index) {
        this.activePage= index
        setTimeout(()=>{
            this.activePageDelay = index;
        }, 1500)
    }
  },
  mounted() {
      let container = document.getElementsByClassName("container")[0];
      container.addEventListener('webkitAnimationEnd ', ()=>{
          console.log(213);
          
      })
  }
};
</script>

<style lang="scss" scoped>
.container {
  height: 100vh;
  overflow: hidden;
  background: linear-gradient(
      -45deg,
      rgb(54, 209, 220),
      rgb(195, 55, 100),
      rgb(91, 134, 229),
      rgb(29, 38, 113)
    )
    0% 0% / 300% 300%;

  .body {
    width: 80%;
    margin: auto;
    display: flex;
    flex-flow: row;
    justify-content: flex-end;
    .content {
      width: 100%;
      position: relative;
      @media screen and (max-width: 1420px) {
        position: relative;
        transform: scale(0.8);
        z-index: 100;
      }
      .upoload-btn {
        width: 480px;
        height: 100px;
        background: #fff;
        position: absolute;
        z-index: 11;
        left: 20%;
        right: -100px;
        top: 50%;
        transform: translateY(-50%);
        transition: 0.5s;
        border-radius: 45px;
        box-shadow: 0px 0px 4px #f2f2f2;
        @media screen and (max-width: 1024px) {
          width: 80vw;
          left: 50%;
        }
        .left-circle,
        .right-circle {
          position: absolute;
          z-index: 11;
          background: #fff;
          width: 150px;
          top: 0;
          height: 90px;
          border-radius: 50px;
          transition: 0.3s;
          text-align: center;
          cursor: pointer;
        }
        .left-circle {
          width: 70%;
          box-sizing: border-box;
          height: 100px;
          .add-file {
            font-size: 35px;
            font-weight: bold;
            line-height: 100px;
            transition: 0.3s;
          }
          &:hover::after {
            content: "文件最大传输尺寸为4G，最多保存72小时";
            font-size: 14px;
            position: absolute;
            width: 150%;
            left: -110px;
            line-height: 20px;
            animation: slide_bottom 0.5s forwards;
          }
          &:hover .add-file {
            line-height: 80px;
          }
          &:hover {
            width: 100%;
            z-index: 20;
          }
        }
        .right-circle {
          height: 86px;
          right: 10px;
          top: 7px;
          background: #f1f1f1;
          &:hover {
            width: calc(100% - 20px);
            z-index: 20;
          }
          &:hover::after {
            content: "文件最大传输尺寸为4G，最多保存168小时";
            font-size: 14px;
            position: absolute;
            width: 150%;
            left: -110px;
            line-height: 20px;
            animation: slide_bottom 0.5s forwards;
          }
          &:hover .login-btn {
            font-size: 22px;
            line-height: 70px;
          }
          .login-btn {
            font-size: 25px;
            font-weight: bold;
            line-height: 85px;
            transition: 0.3s;
          }
          @keyframes slide_bottom {
            0% {
              opacity: 0;
              bottom: 30px;
            }
            100% {
              opacity: 1;
              bottom: 10px;
            }
          }
          // .tip {

          // }
        }
      }
      .slide-left {
        right: -150px;
      }
      .slide-right {
        right: -50px;
      }
    }
    .picture-box {
      @media screen and (max-width: 1024px) {
        right: -1000px;
      }
      position: relative;
      right: 0px;
      min-width: 65vw;
      min-height: 60vh;
      display: flex;
      flex-flow: column;
      justify-content: center;
      align-items: center;
      transition: 0.5s;
      img {
        transition: 0.2s;
      }
      .img-box {
        position: relative;
      }
      .img-top {
        position: absolute;
        top: 0;
        right: 0;
        z-index: 10;
      }
      .img-bottom {
        top: 0;
        right: 0;
        position: relative;
        z-index: 1;
        opacity: 0.8;
      }
      .img-bottom-zoom {
        transform: scale(2);
      }
      @media screen and (max-width: 1420px) {
        .img-bottom-zoom {
          transform: scale(3);
        }
      }
      .zoom-btn {
        position: absolute;
        z-index: 11;
        padding: 10px;
        right: 0px;
        top: 0px;
        width: 30px;
        height: 30px;
        &:hover .solid-square {
          width: 100%;
          height: 100%;
          top: -3px;
          left: -3px;
        }
        .dashed-square {
          position: relative;
          z-index: 10;
          width: 100%;
          height: 100%;
          border-radius: 5px;
          border: 2px dashed #fff;
        }
        .solid-square {
          position: absolute;
          top: 20px;
          left: -10px;
          width: 70%;
          height: 70%;
          border-radius: 4px;
          border: 3px solid #fff;
          transition: 0.3s;
        }
      }
    }
  }
}
.head-box {
  padding-top: 5vh;
  width: 100%;
  height: 10vh;
  display: flex;
  flex-flow: row;
  position: relative;
  z-index: 10;
  .logo-box {
    width: 15%;
    height: 30px;
    position: relative;
    text-align: center;
    padding: auto;
    &::after {
      content: "";
      position: absolute;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 40px;
      height: 40px;
      background: url("https://background.cowtransfer.com/version/1558745225224/image/cow.8b72b0d.png")
        no-repeat;
      background-size: 100%;
    }
  }
  .header {
    width: 85%;
    padding-right: 10%;
    ul {
      display: flex;
      flex-flow: row;
      justify-content: flex-end;
      li {
        margin: 5px 10px;
        padding: 0 15px;
        line-height: 30px;
        font-size: 14px;
        color: #fff;
        cursor: pointer;
        max-height: 30px;
        &:hover:not(last-child) {
          text-shadow: 3px 2px 4px #fdda65;
        }
        &:nth-child(4) {
          font-size: 13px;
          color: #000;
          font-weight: bold;
          background-color: #fdda65;
          border-radius: 50px;
          text-align: center;
          overflow: hidden;
          min-width: 80px;
          transition: 0.3s;
          &:hover {
            min-width: 150px;
          }
        }
      }
    }
  }
}
.footer {
  position: fixed;
  bottom: 20px;
  right: 10%;
  font-size: 12px;
  color: #ccc;
}
img {
  width: auto;
  height: auto;
  max-width: 100%;
  max-height: 100%;
}
.switch-btn {
  width: 50px;
  height: 20px;
  margin: auto;
  margin-top: 5px;
  border: 1px solid #f2f2f2;
  border-radius: 10px;
  position: relative;
  display: flex;
  flex-flow: row;
  justify-content: center;
  align-items: center;
  div {
    font-size: 12px;
    margin: 0 2px;
  }
  .switch-circle {
    position: absolute;
    top: 0;
    width: 20px;
    height: 16px;
    margin-top: 2px;
    background: #eee;
    border-radius: 9px;
    transition: 0.3s;
  }
  .slide-left {
    left: 2px;
  }
  .slide-right {
    left: 24px;
  }
}
.on-active:after {
  content: "";
  position: fixed;
  z-index: 999;
  left: -500px;
  bottom: -1000px;
  width: 1000px;
  height: 1000px;
  background: #a9bcf5;
  border-radius: 50%;
  animation: the_zoom 2s forwards ease-in-out;
  transform: scale(1);
  transform-origin: 0% 100%;
  @keyframes the_zoom {
    0% {
      transform: scale(1);
    }
    50% {
      transform: scale(5);
    }
    100% {
      transform: scale(0);
      transform-origin: 100% 0%;
      left: 100%;
      bottom: 100%;
    }
  }
}
.on-active-body-2:after, .on-active-body-3:after {
  font-family: "宋体";
  position: fixed;
  z-index: 1000;
  font-size: 70px;
  font-weight: 1000;
  color: #fff;
  left: 50%;
  transform: translateX(-50%);
  top: 50%;
  opacity: 0;
  letter-spacing: 10px;
  content: "关于我们";
  animation: slide_top 1.8s forwards ease-in-out;
  @keyframes slide_top {
    0% {
      opacity: 0;
    }
    50% {
      top: 40%;
      opacity: 1;
    }
    100% {
      top: 30%;
      opacity: 0;
    }
  }
}
.on-active-body-3:after {
    content: '意见反馈'
}
#secondPage {
  display: flex;
  flex-flow: column;
  justify-content: center;
  align-items: center;
  .waiting {
    height: 100vh;
    line-height: 80vh;
    color: #fff;
    letter-spacing: 10px;
  }
  .close-btn {
      text-align: center;
      width: 100%;
      height: 30px;
    margin-top: 50px;
    letter-spacing: 5px;
    color: #fff;
    cursor: pointer;
  }
}
</style>
