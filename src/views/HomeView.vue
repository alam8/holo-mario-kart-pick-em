<script setup>
import GroupPicker from "../components/GroupPicker.vue";
import Members from "../data/Members.json";
</script>

<script>
export default {
  data() {
    return {
      groupA: [
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
      groupB: [
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
      groupC: [
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
    };
  },
};
</script>

<template>
  <main>
    <GroupPicker :members="groupA" letter="A" />
    <GroupPicker :members="groupB" letter="B" />
    <GroupPicker :members="groupC" letter="C" />
  </main>
</template>
