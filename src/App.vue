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
          name: "A",
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
          name: "B",
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
          name: "C",
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
      <!-- TODO: Separate rounds using carousel component -->
      <GroupPicker
        v-for="group in groups"
        :key="group"
        :members="group.members"
        :name="group.name"
        round="1"
        v-model="tsuyoFinalists"
      />
      <GroupPicker
        v-for="group in groups"
        :key="group"
        :members="group.members"
        :name="group.name"
        round="2"
        v-model="zakoFinalists"
      />
      <GroupPicker
        :members="tsuyoFinalists"
        name="Tsuyo"
        round="3"
        v-model="tsuyoChampion"
      />
      <GroupPicker
        :members="zakoFinalists"
        name="Zako"
        round="4"
        v-model="zakoChampion"
      />
      <!-- TODO: Results -->
    </div>
  </header>
</template>

<style scoped>
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
