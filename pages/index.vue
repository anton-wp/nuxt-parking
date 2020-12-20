<template>
  <div>
    <TitleBlock id="title" :width="width" :phones="phones" />
    <AdvantagesBlock id="advantages" :width="width" />
    <PriceBlock id="price" :width="width" />
    <ContactBlock id="contact" :width="width" :phones="phones" />
  </div>
</template>

<script>
import TitleBlock from "~/components/TitleBlock";
import AdvantagesBlock from "~/components/AdvantagesBlock";
import PriceBlock from "~/components/PriceBlock";
import ContactBlock from "~/components/ContactBlock";
export default {
  components: {
    TitleBlock,
    AdvantagesBlock,
    PriceBlock,
    ContactBlock,
  },
  data() {
    return {
      width: null,
      phones: ["0951402258", "0974218568"],
    };
  },
  mounted() {
    console.log(this.props);
    this.width = window.innerWidth
  }
};
</script>


<style>
</style>
