<template>
  <div class="advantages-block">
    <h2>
      {{ width > 576 ? AdvantagesBlock.title : AdvantagesBlock.titleMob }}
    </h2>
    <div class="advantages-block__content">
      <div v-for="(block, index) in AdvantagesBlock.blocks" :key="index">
        <div class="content-title">
          <svg class="advantages-block__svg">
            <use :xlink:href="`#${block.Svg}`" />
          </svg>
          <h4>{{ block.title }}</h4>
        </div>
        <span class="content-text">{{ block.content }}</span>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ["width"],
  data: () => ({
    AdvantagesBlock: {
      title: "Почему выбирают именно нашу автостоянку?",
      titleMob: "Почему мы?",
      blocks: [
        {
          Svg: "security",
          title: "Территоря под наблюдением",
          content:
            "Безопасность на высшем уровне. Автостоянка размещена на огражденной территории, охраняется круглосуточно.",
        },
        {
          Svg: "present",
          title: "Выгодно",
          content:
            "Мы предлагаем самые демократичные цены на стоянку для авто в Запорожье. Сейчас это всего 60 грн / в сутки.",
        },
        {
          Svg: "transfer",
          title: "Трансфер",
          content:
            "Трансфер в аэропорт входит в стоимость парковки. Трансфер на микроавтобусах и минивэнах.",
        },
      ],
    },
  }),
};
</script>

<style>
.advantages-block {
  max-width: 1350px;
  margin: 0 auto;
  padding: 175px 15px 0;
}
h2 {
  font-weight: 900;
  font-size: 56px;
  line-height: 150%;
  color: #02133c;
}
h4 {
  font-weight: 900;
  font-size: 21px;
  line-height: 26px;
  color: #02133c;
}
.advantages-block__content {
  flex-wrap: wrap;
  display: flex;
  justify-content: space-around;
}
.advantages-block__svg {
  margin-right: 10px;
  width: 100px;
  height: 100px;
}
.advantages-block__content > div {
  width: 309px;
  /* margin-bottom: 30px; */
  margin: 40px 0;
}
.content-title {
  display: flex;
  align-items: center;
}
.content-text {
  font-size: 18px;
  line-height: 150%;
  letter-spacing: 0.15px;
  color: #4b4b4b;
}
@media (max-width: 900px) {
  h2 {
    text-align: center;
    margin: 30px 0;
    font-size: 50px;
  }
  .advantages-block {
    padding: 60px 10px 0;
  }
}
@media (max-width: 768px) {
  .advantages-block__svg {
    width: 150px;
    height: 150px;
  }
}
@media (max-width: 576px) {
  .advantages-block {
    padding: 30px 10px 0;
  }
  .content-title {
    flex-direction: column;
  }
  h4 {
    display: flex;
    text-align: center;
    line-height: 1.4;
    font-size: 30px;
  }
  h2 {
    text-align: center;
    margin: 30px 0;
    font-size: 50px;
  }
  .content-text {
    display: flex;
    text-align: center;
  }
}
</style>
