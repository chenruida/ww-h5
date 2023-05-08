<script setup lang="ts">
import Images from '@/components/Images'
const datas = ref(Images)
</script>

<template>
  <h1 class="title">武威壁画岩画欣赏</h1>
  <div class="line" v-for="item in datas">
    <div class="img-list">
      <div class="left-arrow arrow">
        <button class="arrow-button">
          <img :src="leftArrow" alt="" />
        </button>
      </div>
      <div class="imgs">
        <ul>
          <li v-for="img in item.items">
            <img :src="img.src" alt="" />
          </li>
        </ul>
      </div>
      <div class="right-arrow arrow">
        <button class="arrow-button">
          <img :src="rightArrow" alt="" />
        </button>
      </div>
    </div>
    <div class="">
      <h2 class="buiding-name">{{ item.build }}</h2>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import leftArrow from '../assets/images/left.png'
import rightArrow from '../assets/images/right.png'
export default defineComponent({
  name: 'HomeView'
})
</script>

<style scoped lang="scss">
.title {
  padding: 2%;
  font-size: 3em;
  text-align: center;
  color: #0d0d0d;
  font-weight: bold;
}
.line {
  // margin-left: 1%;
  height: 18%;
  width: 100%;

  .img-list {
    display: flex;
    height: 80%;
    width: 100%;

    .left-arrow {
      margin-left: 5%;
      margin-right: 2%;
    }
    .right-arrow {
      margin-left: 2%;
      margin-right: 5%;
    }
    .arrow {
      position: relative;
      height: 3rem;
      width: 3rem;
      background-color: transparent;
      margin-top: 6%;
      .arrow-button {
        background-color: transparent;
      }
    }
    .imgs {
      display: flex;
      flex-wrap: nowrap;
      justify-content: center;
      width: 100%;
      overflow: hidden;
      ul {
        display: flex;
        width: 2400px;
        height: 100%;
        /* 注意是给ul设置动画，让整个模块跟着一起动 */
        animation: left_move 3s linear infinite;
        /* 让动画的状态为播放状态 不设置也行，因为是默认状态 */
        animation-play-state: running;
      }
      ul:hover {
        animation-play-state: paused;
      }
      ul li {
        display: flex;
        flex-shrink: 1;
        justify-content: center;
        align-items: center;
        width: 200px;
        height: 100%;
        margin-left: 30px;
      }
      img {
        width: 200px;
        height: 100%;
      }
      // img {
      //   width: 100%;
      //   height: 100%;
      //   margin-right: 10px;
      //   background-color: gray;
      //   border-right: 1px solid;
      //   text-align: center;
      //   flex-shrink: 0;
      //   line-height: 50px;
      // }
    }
  }

  .buiding-name {
    text-align: center;
    color: #0d0d0d;
    font-size: 1.5em;
    padding: 1em;
  }
}

@keyframes left_move {
  to {
    /* 这里偏移的应该是8个盒子的长度，留下四个相同的盒子补上空缺造成视觉差 */
    transform: translateX(-1600px);
  }
}
</style>
