<template>
  <div class="text-center">
    <v-bottom-sheet v-model="sheet">
      <template v-slot:activator="{ on, attrs }">
        <v-btn color="main" v-bind="attrs" v-on="on" class="white--text" rounded large>
          <v-icon class="picture">mdi-camera</v-icon>사진 찍기
        </v-btn>
      </template>
      <v-list class="text-center">
        <v-subheader><strong>촬영 모드</strong>를 선택해주세요.</v-subheader>
        <v-list-item v-for="tile in tiles" :key="tile.title" @click="sheet = false">
          <v-list-item-title @click="mode(tile.mode)">{{ tile.title }}</v-list-item-title>
        </v-list-item>
        <v-col>
          <v-btn @click="cancel()" block elevation="0" large color="sub">취소</v-btn>
        </v-col></v-list
      >
    </v-bottom-sheet>
  </div>
</template>
<script>
export default {
  data: () => ({
    sheet: false,
    tiles: [
      { img: 'keep.png', mode: '알약', title: '알약 찍기💊' },
      { img: 'inbox.png', mode: '처방전', title: '처방전, 약 봉투 찍기📃' },
    ],
  }),
  methods: {
    cancel() {
      this.sheet = false;
    },
    mode(n) {
      this.$router.push({ name: 'Camera', params: { cameraMode: n } });
    },
  },
};
</script>
<style scoped>
.picture {
  padding-right: 8px;
}
.v-subheader {
  display: inline-flex;
}
</style>
