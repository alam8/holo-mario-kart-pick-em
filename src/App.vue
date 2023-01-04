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
      tsuyoFinalists: [],
      zakoFinalists: [],
      tsuyoChampion: [],
      zakoChampion: [],
    };
  },
};
</script>

<template>
  <header>
    <div class="wrapper">
      <h1>hololive New Year Cup 2023 Pick'em</h1>
      <b-card no-body>
        <b-tabs pills card end>
          <b-tab title="Group Stage: Tsuyo" active>
            <GroupPicker
              v-for="group in groups"
              :key="group"
              :members="group.members"
              :name="group.name"
              round="1"
              v-model="tsuyoFinalists"
            />
          </b-tab>
          <b-tab title="Group Stage: Zako">
            <GroupPicker
              v-for="group in groups"
              :key="group"
              :members="group.members"
              :name="group.name"
              round="2"
              v-model="zakoFinalists"
            />
          </b-tab>
          <b-tab title="Finals">
            <GroupPicker
              :members="tsuyoFinalists"
              name="Tsuyo Cup Finalists"
              round="3"
              v-model="tsuyoChampion"
            />
            <GroupPicker
              :members="zakoFinalists"
              name="Zako Cup Finalists"
              round="4"
              v-model="zakoChampion"
            />
          </b-tab>
          <b-tab title="Results">
            <GroupPicker
              :members="tsuyoChampion"
              name="Tsuyo Champion"
              round="5"
            />
            <GroupPicker
              :members="zakoChampion"
              name="Zako Champion"
              round="6"
            />
          </b-tab>
        </b-tabs>
      </b-card>
    </div>
  </header>
</template>

<style scoped>
.card-header-tabs .nav-link.active {
  background-color: var(--bs-nav-pills-link-active-bg) !important;
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
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
    grid-column-start: 1;
    justify-content: center;
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
