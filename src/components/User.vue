<template>
  <div class="component">
    <h1>The User Component</h1>
    <p>I'm an awesome User!</p>
    <button @click="changeName">Change my Name</button>
    <p>Name is {{ name }}</p>
    <hr />
    <div class="row">
      <div class="col-xs-12 col-sm-6">
        <!-- name pertama dari child => UserDatail.vue -->
        <!-- name kedua dari parent => User.vue -->
        <!-- nama fungsi dari child = UserDetail.vue @nameWasReset="variabel_parent(User.vue) = variabel_child(UserDetail.vue)" -->
        <!-- nama fungsi resetFn="nama_fungsi" utk child => UserDetail.vue -->
        <app-user-detail 
            :myName="name"
            @nameWasReset="name = $event"
            :resetFn="resetName">
        </app-user-detail>
      </div>
      <div class="col-xs-12 col-sm-6">
        <app-user-edit></app-user-edit>
      </div>
    </div>
  </div>
</template>

<script>
import UserDetail from "./UserDetail.vue";
import UserEdit from "./UserEdit.vue";

export default {
  data() {
    return {
      //variabel name
      name: "Max"
    };
  },
  methods: {
    changeName() {
      //ubah nilai name
      this.name = "Anna"; //jgn lupa titik koma
    },
    //reset name untk komunikasi ke child => UserDetail.vue
    resetName() {
      this.name = "Max";
    }
  },
  components: {
    appUserDetail: UserDetail,
    appUserEdit: UserEdit
  }
};
</script>

<style scoped>
div {
  background-color: lightblue;
}
</style>
