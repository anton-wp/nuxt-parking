<template>
  <div class="title-block">
    <div class="title-block__opacity"></div>
    <img
      v-show="loadImg"
      :src="width ? (width > 576 ? titleBlock.imgBig : titleBlock.imgMob) : ''"
      alt="ой что-то пошло не так"
      @load="loaded"
    />
    <div class="title-block__content">
      <h1>{{ titleBlock.title }}</h1>
      <h3>{{ titleBlock.subTitle }}</h3>
      <div class="title-block__subTitle">
        <div v-for="(item, index) in titleBlock.content" :key="index">
          <!-- <svg width="41" height="41" class="title-block__svg-big">
            <use :xlink:href="`#${item.imgSVG}`" />
          </svg> -->
          <div
            v-if="index === 1"
            class="block-info"
            style="margin: 15px 0 15px 15px; width: 250px; position: relative"
          >
            <h6>{{ item.title }}</h6>
            <div
              v-for="(block, index) in item.subTitle"
              :key="index"
              style="display: flex; align-items: center"
            >
              <a :href="`tel:+38${block}`">
                {{ block }}
              </a>
              <div
                v-if="index === 0"
                style=" margin-left: 7px; display: flex; position: absolute; right: -20px;"
              >
                <a
                  :href="`viber://add?number=38${block}`"
                  style="margin: 0 7px"
                >
                  <svg width="25" height="25" class="title-block__svg">
                    <use xlink:href="#viberWhite" />
                  </svg>
                </a>
                <a href="https://teleg.run/airParking">
                  <svg width="25" height="25" class="title-block__svg">
                    <use xlink:href="#telegramWhite" /></svg
                ></a>
              </div>
            </div>
          </div>
          <div
            v-else
            style="margin: 15px 0 15px 15px; width: 200px"
            class="block-info"
          >
            <h6>{{ item.title }}</h6>
            <span v-for="(block, index) in item.subTitle" :key="index">
              {{ block }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["phones", "width"],
  data() {
    return {
      titleBlock: {
        imgBig: require("../assets/Title-image.webp"),
        imgMob: require("../assets/HERO_mob.webp"),
        title: "Стоянка aэропорт Запорожье",
        subTitle: "Комфортный трансфер",
        content: [
          {
            imgSVG: "clock",
            title: "Часы работы",
            subTitle: ["Круглосуточно"],
          },
          {
            imgSVG: "phone",
            title: "Свяжитесь с нами",
            subTitle: this.phones,
          },
        ],
      },
      loadImg: false,
    };
  },
  methods: {
    loaded() {
      this.loadImg = true;
    },
  },
};
</script>

<style>
.title-block {
  margin-top: -72px;
  position: relative;
  height: 785px;
}
.block-info {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.title-block__opacity {
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: 2;
  background: #000000;
  opacity: 0.6;
}
.title-block > img {
  z-index: 1;
  position: absolute;
  object-fit: cover;
  width: 100%;
  height: 785px;
  animation: eye 0.5s ease-in-out;
}

@keyframes eye {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

.title-block__content {
  padding-top: 162px;
  display: flex;
  justify-content: center;
  flex-direction: column;
  z-index: 3;
  max-width: 971px;
  margin: 0 auto;
}
h1 {
  margin: 0;
  z-index: 3;
  font-weight: 900;
  font-size: 100px;
  line-height: 109.5%;
  color: #ffffff;
  text-align: center;
}
h3 {
  z-index: 3;
  font-size: 36px;
  line-height: 109.5%;
  text-align: center;
  color: #ffffff;
}
h6 {
  font-size: 26px;
  font-weight: 500;
  margin: 10px 0;
}
span {
  font-size: 26px;
}
a {
  display: flex;
  cursor: pointer;
  text-decoration: none;
  color: white;
  margin: 10px 0;
  font-size: 26px;
  font-weight: 400;
}
.title-block__subTitle {
  z-index: 4;
  display: flex;
  justify-content: center;
  color: white;
}
.title-block__subTitle > div {
  display: flex;
  justify-content: center;
  margin: 0 30px;
  height: 100%;
}
.title-block__svg {
  margin: auto;
}
.title-block__svg-big {
  margin-top: 40px;
}

@media (max-width: 768px) {
  h1 {
    font-size: 75px;
  }
  h3 {
    font-size: 30px;
  }
  a {
    font-size: 25px;
  }
}
@media (max-width: 576px) {
  h1 {
    font-size: 58px;
  }
  h3 {
    font-size: 26px;
  }
  a {
    font-size: 25px;
  }
  .title-block__subTitle {
    flex-wrap: wrap;
  }
}
</style>
