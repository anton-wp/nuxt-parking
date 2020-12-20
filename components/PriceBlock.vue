<template>
  <div class="price-block">
    <h2>{{ priceBlock.title }}</h2>
    <div class="price-block__content">
      <div class="price-block__price">
        <div
          v-for="(item, index) in priceBlock.prices"
          :key="index"
          class="price"
        >
          {{ item }}
          <span v-if="index !== 0">(трансфер включен в стоимость)</span>
        </div>
      </div>
      <div v-if="width > 900" class="price-block__image">
        <img :src="priceBlock.img" alt="ой что-то пошло не так" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['width'],
  data: () => ({
    priceBlock: {
      title: "Наши цены",
      img: require("../assets/imgPrice.webp"),
      prices: [
        "60 грн - 1 день",
        "300 грн - 3 день",
        "500 грн - 7 дней",
        "700 грн - 10 дней",
      ],
    },
  }),
};
</script>
<style>
.price-block {
  max-width: 1350px;
  padding: 175px 15px 0;
  margin: 0 auto;
}
.price {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  height: 103px;
  background: #ffffff;
  border: 1px dashed #2693ff;
  box-sizing: border-box;
  box-shadow: 0px 4px 15px rgba(210, 210, 210, 0.25);
  border-radius: 10px;

  font-weight: 900;
  font-size: 42px;
  line-height: 48px;
  color: #2693ff;
  margin: 12.5px 0;
}
.price > span {
  /* color: black; */
  font-size: 18px;
  font-weight: 500;
}
.price-block__content {
  overflow: hidden;
  display: flex;
}
.price-block__price {
  width: 40%;
  flex: 0 0 40%;
}
.price-block__image {
  width: 60%;
  flex: 0 0 60%;
  padding-left: 104px;
}
.price-block__image > img {
  max-width: 100%;
  height: 100%;
  object-fit: cover;
}

@media (max-width: 1100px) {
  .price-block__price {
    width: 50%;
    flex: 0 0 50%;
  }
  .price-block__image {
    width: 60%;
    flex: 0 0 50%;
    padding-left: 50px;
  }
}
@media (max-width: 900px) {
  .price-block {
    padding: 60px 10px 0;
  }
  .price-block__price {
    width: 100%;
    flex: 0 0 100%;
  }
}
@media (max-width: 576px) {
  .price-block {
    padding: 0px 15px 0;
  }
}
@media (max-width: 420px) {
  .price {
    font-size: 32px;
  }
  .price > span {
    font-size: 16px;
  }
}
</style>

