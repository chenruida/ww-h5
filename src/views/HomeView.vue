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
      <div class="imgs" v-for="img in item.imgs">
        <img :src="item.src" alt="" />
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
  font-size: 30px;
  text-align: center;
  color: #0d0d0d;
  font-weight: bold;
}
.line {
  // margin-left: 1%;
  height: 17%;
  width: 100%;

  .img-list {
    display: flex;

    .left-arrow {
      margin-left: 5%;
    }
    .right-arrow {
      margin-right: 5%;
    }
    .arrow {
      height: 30px;
      width: 30px;
      background-color: transparent;
      .arrow-button {
        background-color: transparent;
      }
    }
    .imgs {
      width: 100%;
      color: #000;
    }
  }

  .buiding-name {
    text-align: center;
    color: #0d0d0d;
    font-size: 20px;
    margin-top: 20px;
    margin-bottom: 15px;
  }
}
</style>
