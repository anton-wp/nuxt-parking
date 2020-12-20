<template>
  <div class="header">
    <div class="header-background"></div>
    <div class="header-container">
      <svg
        @click="scrollToComment('title')"
        width="121"
        height="44"
        style="cursor: pointer"
      >
        <use xlink:href="#logo" />
      </svg>
      <svg
        v-if="width < 900"
        @click="show = !show"
        width="40"
        height="40"
        style="cursor: pointer; margin-left: auto; z-index: 1; fill: white"
      >
        <use xlink:href="#burger" />
      </svg>
      <ul v-if="width > 900" class="header-menu">
        <a
          v-for="(item, index) in menu"
          :key="index"
          @click="scrollToComment(item.slug)"
          >{{ item.title }}</a
        >
      </ul>
      <transition name="fade">
        <div v-if="show && width < 900" class="block-burger">
          <div
            style="font-size: 28px; line-height: 2.5"
            v-for="(item, index) in menu"
            :key="index"
            @click="
              () => {
                show = false;
                scrollToComment(item.slug);
              }
            "
          >
            {{ item.title }}
          </div>
          <div style="display: flex; flex-direction: column">
            <div v-for="item in phones" :key="item">
              <a :href="`tel:+38${item}`" style="font-size: 24px">{{ item }}</a>
              <div
                v-if="item === '0951402258'"
                class="block-burger__button"
                style="
                  margin-left: 7px;
                  display: flex;
                  position: absolute;
                  bottom: 0;
                  width: 100%;
                  left: 0;
                  display: flex;
                  justify-content: space-around;
                "
              >
                <a :href="`viber://add?number=38${item}`" style="margin: 0 7px">
                  <svg width="50" height="50" class="title-block__svg">
                    <use xlink:href="#viber" />
                  </svg>
                </a>
                <a href="https://teleg.run/airParking">
                  <svg width="50" height="50" class="title-block__svg">
                    <use xlink:href="#telegram" /></svg
                ></a>
              </div>
            </div>
          </div>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      phones: ["0951402258", "0974218568"],
      width: null,
      show: false,
      menu: [
        {
          title: "Главная",
          slug: "title",
        },
        {
          title: "О нас",
          slug: "advantages",
        },
        {
          title: "Цены",
          slug: "price",
        },
        {
          title: "Контакты",
          slug: "contact",
        },
      ],
    };
  },
  methods: {
    scrollToComment(el) {
      if (document.getElementById(el)) {
        document.getElementById(el).scrollIntoView({
          behavior: "smooth",
          inline: "nearest",
        });
      }
    },
  },
  mounted() {
    this.width = window.innerWidth;
  },
};
</script>


<style>
.header {
  z-index: 5;
  position: sticky;
  height: 72px;
  top: 0;
  width: 100%;
  display: flex;
  align-items: center;
}
.header-container {
  padding: 0 25px;
  max-width: 1350px;
  width: 100%;
  display: flex;
  position: relative;
  margin: 0 auto;
  align-items: center;
}
.header-container > svg {
  z-index: 3;
}
.header-background {
  width: 100%;
  height: 72px;
  position: absolute;
  background: rgba(0, 0, 0, 1);
  /* opacity: 0.5; */
  z-index: 1;
}
.header-menu {
  z-index: 3;
  display: flex;
  font-weight: 700;
  font-size: 18px;
  color: white;
  margin-left: auto;
}
.header-menu > a {
  cursor: pointer;
  display: block;
  margin-left: 38px;
}
.block-burger {
  overflow: hidden;
  position: fixed;
  width: 100vw;
  height: 100vh;
  left: 0;
  top: 0;
  background-color: black;
  display: flex;
  align-items: center;
  color: white;
  justify-content: center;
  flex-direction: column;
  opacity: 1;
}
.fade-enter-active,
.fade-leave-active {
  transition: margin 0.5s;
}
.fade-enter,
.fade-leave-to {
  margin-top: -100vh;
}
.block-burger__button {
  padding-bottom: 55px;
}
@media (max-width: 576px) {
  .title-block__subTitle > div {
    min-width: 250px;
  }
}
@media (max-width: 360px) {
  .block-burger__button {
    padding-bottom: 25px;
  }
}
</style>
