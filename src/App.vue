<script setup>
import GroupPicker from "./components/GroupPicker.vue";
import GroupData from "./data/GroupData.js";
</script>

<script>
export default {
  data() {
    return {
      groups: GroupData.groups,
      tsuyoFinalistsA: [],
      tsuyoFinalistsB: [],
      tsuyoFinalistsC: [],
      zakoFinalistsA: [],
      zakoFinalistsB: [],
      zakoFinalistsC: [],
      tsuyoChampion: [],
      zakoChampion: [],
    };
  },
  computed: {
    tsuyoFinalists() {
      return this.tsuyoFinalistsA.concat(
        this.tsuyoFinalistsB,
        this.tsuyoFinalistsC
      );
    },
    zakoFinalists() {
      return this.zakoFinalistsA.concat(
        this.zakoFinalistsB,
        this.zakoFinalistsC
      );
    },
  },
  methods: {
    getGroupLetter: function (name) {
      return name.slice(-1);
    },
    finalistsNotSelected(size) {
      return !(
        this.tsuyoFinalists.length === size &&
        this.zakoFinalists.length === size
      );
    },
    champsNotSelected(size) {
      return !(
        this.tsuyoChampion.length === size && this.zakoChampion.length === size
      );
    },
  },
};
</script>

<template>
  <header>
    <div class="wrapper">
      <h1 id="title">hololive New Year Cup 2023 Pick'em</h1>
      <b-card class="group-card" no-body>
        <b-tabs pills justified lazy>
          <b-tab class="group-body" title="Group Stage: Tsuyo" active>
            <GroupPicker
              v-for="group in groups"
              :key="group"
              :members="group.members"
              :name="group.name"
              round="1"
              v-model="this['tsuyoFinalists' + getGroupLetter(group.name)]"
              :winnersCount="GroupData.FINALISTS_PER_GROUP"
              :complement="zakoFinalists"
              :champions="[]"
            />
          </b-tab>
          <b-tab class="group-body" title="Group Stage: Zako">
            <GroupPicker
              v-for="group in groups"
              :key="group"
              :members="group.members"
              :name="group.name"
              round="1"
              v-model="this['zakoFinalists' + getGroupLetter(group.name)]"
              :winnersCount="GroupData.FINALISTS_PER_GROUP"
              :complement="tsuyoFinalists"
              :champions="[]"
            />
          </b-tab>
          <b-tab
            class="group-body"
            title="Finals"
            :disabled="
              finalistsNotSelected(
                GroupData.FINALISTS_PER_GROUP * GroupData.NUMBER_OF_GROUPS
              )
            "
          >
            <GroupPicker
              :members="tsuyoFinalists"
              name="Tsuyo Cup Finalists"
              round="3"
              v-model="tsuyoChampion"
              :winnersCount="GroupData.PODIUM_SIZE"
              :complement="[]"
              :champions="tsuyoChampion"
            />
            <GroupPicker
              :members="zakoFinalists"
              name="Zako Cup Finalists"
              round="4"
              v-model="zakoChampion"
              :winnersCount="GroupData.PODIUM_SIZE"
              :complement="[]"
              :champions="zakoChampion"
            />
          </b-tab>
          <!-- <b-tab
            class="group-body"
            title="Results"
            :disabled="champsNotSelected(GroupData.PODIUM_SIZE)"
          >
            <GroupPicker
              :members="tsuyoChampion"
              name="Tsuyo Champion"
              round="5"
              winnersCount="1"
            />
            <GroupPicker
              :members="zakoChampion"
              name="Zako Champion"
              round="6"
              winnersCount="1"
            />
          </b-tab> -->
        </b-tabs>
      </b-card>
    </div>
  </header>
</template>

<style scoped>
#title {
  margin-bottom: 1.5rem;
}

.group-card {
  background: var(--color-background);
  border: 0px;
}

.group-body {
  margin-top: 1.5rem;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  font-size: 12px;
  text-align: center;
  margin-top: 12rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  .wrapper {
    margin-left: -3.85vw;
  }

  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
    grid-column-start: 1;
    justify-content: center;
  }

  .group-card {
    width: 75vw;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    margin-left: -1rem;
    font-size: 1rem;
    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
