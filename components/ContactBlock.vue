<template>
  <div class="contact-block">
    <img
      :src="width > 576 ? contactBlock.imgBig : contactBlock.imgMob"
      alt="ой что-то пошло не так"
    />

    <div class="contact-block__content">
      <h2 class="conten-block__title">{{ contactBlock.title }}</h2>
      <div
        v-for="(item, index) in contactBlock.content"
        :key="index"
        class="contact-block__wrapper"
      >
        <svg width="33" height="33" class="contact-block__svg">
          <use :xlink:href="`#${item.img}`" />
        </svg>
        <div v-if="index === 1" style="margin-top: 20px">
          <span
            v-for="(text, index) in item.texts"
            :key="index"
            class="contact-block__phone"
            style="display: flex; color: white; margin: 10px 0"
            >{{ text }}</span
          >
        </div>
        <div v-else>
          <div
            v-for="(text, index) in item.texts"
            :key="index"
            class="contact-block__social-wrapper"
          >
            <a :href="`tel:+38${text}`" class="contact-block__phone">{{
              text
            }}</a>

            <div v-if="index === 0" class="block-svg__social">
              <a :href="`viber://add?number=38${text}`" style="margin: 0 7px">
                <svg
                  width="25"
                  height="25"
                  class="title-block__svg"
                  style="fill: white"
                >
                  <use xlink:href="#viberWhite" />
                </svg>
              </a>
              <a href="https://teleg.run/airParking">
                <svg
                  width="25"
                  height="25"
                  class="title-block__svg"
                  style="fill: white"
                >
                  <use xlink:href="#telegramWhite" /></svg
              ></a>
            </div>
          </div>
        </div>
      </div>
    </div>
    <iframe
      v-if="iframe"
      class="contact-block__map"
      src="https://www.google.com/maps/d/u/0/embed?mid=1A-13bU_yCc_c8v5XK03HU8glj-lQiI2H&z=13"
      width="640"
      height="480"
    
    ></iframe>
  </div>
</template>
<script>
export default {
  props: ["phones", "width"],
  data() {
    return {
      iframe: false,
      contactBlock: {
        imgBig: require("../assets/Contact.webp"),
        imgMob: require("../assets/Footer_mob.webp"),
        title: "Контакты",
        content: [
          {
            img: "phoneWhite",
            texts: this.phones,
          },
          {
            img: "local",
            texts: ["г. Запорожье", "ул. Военстрой 200"],
          },
        ],
      },
    };
  },
  mounted() {
    setTimeout(() => {
      this.iframe = true;
    }, 2000);
  },
};
</script>
<style>
.contact-block {
  margin-top: 180px;
  position: relative;
}
.contact-block > img {
  position: absolute;
  width: 100%;
  z-index: -1;
  height: 620px;
  object-fit: cover;
}
.conten-block__title {
  color: white;
}
.contact-block__content {
  max-width: 1350px;
  margin: 0 auto;
  padding: 100px 15px 20px;
}
.contact-block__svg {

  margin-right: 20px;
}
.contact-block__map {
  position: absolute;
  top: 0;
  right: 0;
  width: 60%;
  height: 615px;
  border: none;
}
.contact-block__wrapper {
  display: flex;
  align-items: center;
}
.contact-block__social-wrapper {
  display: flex;
  align-items: center;
  position: relative;
}
.block-svg__social {
  margin-left: 7px;
  display: flex;
  position: absolute;
  top: 2px;
  right: -70px;
}
@media (max-width: 900px) {
  .contact-block__map {
    margin-top: 50px;
    width: 100%;
    position: relative;
  }
/* }
@media (max-width: 576px) { */
  .contact-block__social-wrapper {
    display: flex;
    color: white;
    margin-bottom: 10px;
    justify-content: center;
    position: relative;
  }
  .block-svg__social {
    top: 7px;
  }

  .conten-block__title {
    margin-bottom: 10px;
  }
  .contact-block {
    margin-top: 70px;
  }
  .contact-block__svg {
    display: none;
  }
  .contact-block__content {
    padding: 10px 15px 20px;
  }
  .contact-block__wrapper {
    justify-content: center;
  }
  .contact-block__phone {
    font-size: 30px;
    justify-content: center;
  }
}
</style>
