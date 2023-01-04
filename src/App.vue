<script setup>
import GroupPicker from "./components/GroupPicker.vue";
import Members from "./data/Members.json";
</script>

<script>
export default {
  data() {
    return {
      groups: [
        {
          name: "Group A",
          members: [
            Members.Matsuri,
            Members.Fubuki,
            Members.Okayu,
            Members.Marine,
            Members.Towa,
            Members.Nene,
            Members.Chloe,
            Members.Iroha,
            Members.Ame,
            Members.Kronii,
            Members.Moona,
            Members.Anya,
          ],
        },
        {
          name: "Group B",
          members: [
            Members.Roboco,
            Members.Miko,
            Members.Mel,
            Members.Suisei,
            Members.Haachama,
            Members.Ayame,
            Members.Watame,
            Members.Luna,
            Members.Lamy,
            Members.Gura,
            Members.Kaela,
            Members.Kobo,
          ],
        },
        {
          name: "Group C",
          members: [
            Members.Sora,
            Members.Aki,
            Members.Choco,
            Members.Subaru,
            Members.Mio,
            Members.Pekora,
            Members.Noel,
            Members.Lui,
            Members.Koyori,
            Members.Ollie,
            Members.Reine,
            Members.Zeta,
          ],
        },
      ],
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
              :members="groups[0].members"
              :name="groups[0].name"
              round="1"
              v-model="tsuyoFinalistsA"
              winnersCount="4"
            />
            <GroupPicker
              :members="groups[1].members"
              :name="groups[1].name"
              round="1"
              v-model="tsuyoFinalistsB"
              winnersCount="4"
            />
            <GroupPicker
              :members="groups[2].members"
              :name="groups[2].name"
              round="1"
              v-model="tsuyoFinalistsC"
              winnersCount="4"
            />
          </b-tab>
          <b-tab class="group-body" title="Group Stage: Zako">
            <GroupPicker
              :members="groups[0].members"
              :name="groups[0].name"
              round="1"
              v-model="zakoFinalistsA"
              winnersCount="4"
            />
            <GroupPicker
              :members="groups[1].members"
              :name="groups[1].name"
              round="1"
              v-model="zakoFinalistsB"
              winnersCount="4"
            />
            <GroupPicker
              :members="groups[2].members"
              :name="groups[2].name"
              round="1"
              v-model="zakoFinalistsC"
              winnersCount="4"
            />
          </b-tab>
          <b-tab class="group-body" title="Finals">
            <GroupPicker
              :members="tsuyoFinalists"
              name="Tsuyo Cup Finalists"
              round="3"
              v-model="tsuyoChampion"
              winnersCount="3"
            />
            <GroupPicker
              :members="zakoFinalists"
              name="Zako Cup Finalists"
              round="4"
              v-model="zakoChampion"
              winnersCount="3"
            />
          </b-tab>
          <b-tab class="group-body" title="Results">
            <!-- TODO: Use different component to show results instead of GroupPicker -->
            <!-- <GroupPicker
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
            /> -->
          </b-tab>
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
