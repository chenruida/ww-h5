<script setup lang="ts">
import Images from '@/components/Images'
const datas = ref(Images)
const carousel = ref<any>([])
const leftClick = (index: number) => {
  carousel.value[index].prev()
}
const rightClick = (index: number) => {
  carousel.value[index].next()
}
onMounted(() => {
  console.log(carousel.value)
})
</script>

<template>
  <h1 class="title">武威壁画岩画欣赏</h1>
  <div class="line" v-for="(item, index) in datas" :key="index">
    <div class="img-list">
      <div class="left-arrow arrow">
        <button class="arrow-button" @click="leftClick(index)">
          <img :src="leftArrow" alt="" />
        </button>
      </div>
      <div class="imgs">
        <el-carousel :interval="6000" type="card" arrow="never" ref="carousel">
          <el-carousel-item v-for="(img, imIgndex) in item.items" :key="imIgndex">
            <button>
              <el-image windth="500px" :src="img.src" />
            </button>
          </el-carousel-item>
        </el-carousel>
      </div>
      <div class="right-arrow arrow">
        <button class="arrow-button" @click="rightClick(index)">
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
import { defineComponent, ref, onMounted } from 'vue'
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
    justify-content: center;
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
      height: 3rem;
      width: 3rem;
      background-color: transparent;
      line-height: 300px;
    }
    .imgs {
      width: 70%;
      .el-carousel__item {
        display: flex;
        justify-content: center;
      }

      .el-carousel__item:nth-child(2n) {
        background-color: transparent;
      }

      .el-carousel__item:nth-child(2n + 1) {
        background-color: transparent;
      }
    }
  }

  .buiding-name {
    text-align: center;
    color: #0d0d0d;
    font-size: 1.5em;
    padding: 1em;
  }
}

button {
  background-color: transparent;
  border: none;
}
</style>
