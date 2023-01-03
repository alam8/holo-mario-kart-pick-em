<script setup>
import GroupPicker from "../components/GroupPicker.vue";
import Members from "../data/Members.json";
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
    };
  },
};
</script>

<template>
  <main>
    <GroupPicker
      v-for="group in groups"
      :key="group"
      :members="group.members"
      :name="group.name"
      v-model="tsuyoFinalists"
    />
    <GroupPicker :members="tsuyoFinalists" name="Tsuyo" />
  </main>
</template>
