<template>
  <div class="letter-result" :style="style" :key="typedLetter">
    <div v-if="isSuccess" class="success">
      <Letter :value="typedLetter" />
      <br />
      <span>Good!</span>
      <br />
      <span>+1</span>
    </div>
    <div v-else class="failure">
      <Letter :value="typedLetter" />
      <br />
      <span>Try again.</span>
      <br />
      <span>Back to 0</span>
    </div>
  </div>
</template>

<script>
import Letter from "@/components/Letter.vue";
import { toRefs, ref, watch } from "vue";

export default {
  name: "LetterResult",
  components: {
    Letter,
  },
  props: {
    isSuccess: {
      type: Boolean,
      required: true,
    },
    typedLetter: {
      type: String,
      required: true,
    },
  },
  setup(props) {
    const { typedLetter } = toRefs(props);
    const style = ref({});

    const animate = () => {
      style.value = {
        animation: "1s slide-bottom",
      };
    };

    watch(typedLetter, () => {
      animate();
    });

    return { style };
  },
};
</script>

<style lang="scss" scoped>
.letter-result {
  position: absolute;
  top: 46vh;
  opacity: 0;
  text-align: center;

  .success {
    color: green;
  }
  .failure {
    color: darkred;
  }
}
</style>
