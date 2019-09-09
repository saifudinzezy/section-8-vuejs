<template>
  <div class="component">
    <h3>You may view the User Details here</h3>
    <p>Many Details</p>
    <!-- pangil key utk mengubah nilai name yg nantinya akan dipanggil oleh parent -->
    <p>User name: {{ switchName() }}</p>
    <button @click="resetName">Reset Name</button>
    <!-- pangil nama fungsi yg sdh di ambil parent ditampung di props -->
    <button @click="resetFn()">Reset Name</button>
  </div>
</template>

<script>
export default {
  //key untuk parrent
  //validasi
  props: {
    myName: {
      //hanya menerima inputan string jika mau byk simpan diarray
      myName: String,
      required: true, //harus diisi
      default: "Max" //defauld nilai
    },
    //tangkap fungsi resetFn kiriman dari parent => User.vue 
     resetFn: Function
  },
  methods: {
    switchName() {
      //
      return this.myName
        .split("")
        .reverse()
        .join("");
    },
    resetName() {
      //reset name
      this.myName = "Max";
      //emit(nama_listener, datas)
      //fungsi utk komunikasi / kirim data ke parent => User.vue  dari child UserDetail.vue
      this.$emit("nameWasReset", this.myName);
    }
  }
};
</script>

<style scoped>
div {
  background-color: lightcoral;
}
</style>
