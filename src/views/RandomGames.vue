<template>
  <component :is="game" />
  <div class="credits">
    <span>
      By <a href="https://timothecrespy.fr">Tim</a> on
      <a href="https://github.com/TimotheCrespy/random-games.timothecrespy"
        >🐙</a
      >
      with
      <a href="https://en.wikipedia.org/wiki/Love">❤️</a> and
      <a href="https://v3.vuejs.org/">Vue 3</a>
    </span>
  </div>
</template>

<script>
import { ref, markRaw } from "vue";
import NextLetter from "@/components/games/NextLetter";
import PreviousLetter from "@/components/games/PreviousLetter";

import CanadaProvinces from "@/components/games/geographic-entities/CanadaProvinces";
import ChinaProvinces from "@/components/games/geographic-entities/ChinaProvinces";
import FranceDepartments from "@/components/games/geographic-entities/FranceDepartments";
import GermanyLands from "@/components/games/geographic-entities/GermanyLands";
import SpainProvinces from "@/components/games/geographic-entities/SpainProvinces";
import USStates from "@/components/games/geographic-entities/USStates";

import CanadaProvinceCodes from "@/components/games/geographic-entity-codes/CanadaProvinceCodes";
import ChinaProvinceCodes from "@/components/games/geographic-entity-codes/ChinaProvinceCodes";
import FranceDepartmentCodes from "@/components/games/geographic-entity-codes/FranceDepartmentCodes";
import GermanyLandCodes from "@/components/games/geographic-entity-codes/GermanyLandCodes";
import SpainProvinceCodes from "@/components/games/geographic-entity-codes/SpainProvinceCodes";
import USStateCodes from "@/components/games/geographic-entity-codes/USStateCodes";

import CanadaProvinceNames from "@/components/games/geographic-entity-names/CanadaProvinceNames";
import ChinaProvinceNames from "@/components/games/geographic-entity-names/ChinaProvinceNames";
import FranceDepartmentNames from "@/components/games/geographic-entity-names/FranceDepartmentNames";
import GermanyLandNames from "@/components/games/geographic-entity-names/GermanyLandNames";
import SpainProvinceNames from "@/components/games/geographic-entity-names/SpainProvinceNames";
import USStateNames from "@/components/games/geographic-entity-names/USStateNames";

export default {
  name: "RandomGames",
  setup() {
    const game = ref(null);
    const games = ref([
      markRaw(NextLetter),
      markRaw(PreviousLetter),

      markRaw(CanadaProvinces),
      markRaw(ChinaProvinces),
      markRaw(FranceDepartments),
      markRaw(GermanyLands),
      markRaw(SpainProvinces),
      markRaw(USStates),

      markRaw(CanadaProvinceCodes),
      markRaw(ChinaProvinceCodes),
      markRaw(FranceDepartmentCodes),
      markRaw(GermanyLandCodes),
      markRaw(SpainProvinceCodes),
      markRaw(USStateCodes),

      markRaw(CanadaProvinceNames),
      markRaw(ChinaProvinceNames),
      markRaw(FranceDepartmentNames),
      markRaw(GermanyLandNames),
      markRaw(SpainProvinceNames),
      markRaw(USStateNames),
    ]);
    game.value = games.value[Math.floor(Math.random() * games.value.length)];

    return { game };
  },
};
</script>

<style lang="scss" scoped>
.credits {
  position: fixed;
  display: flex;
  justify-content: center;
  bottom: 0;
  width: 100%;
  color: #fff;
  margin-bottom: 1rem;

  a {
    text-decoration: underline;
    color: #fff;

    &:hover {
      text-decoration: none;
    }
  }
}
</style>