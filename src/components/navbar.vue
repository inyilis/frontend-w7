<template>
  <nav class="dropdown">
    <button
      class="btn"
      type="button"
      id="dropdownMenuButton"
      data-toggle="dropdown"
    >
      <img src="../assets/menu.png" alt="" />
    </button>
    <div class="dropdown-menu text-center" aria-labelledby="dropdownMenuButton">
      <router-link to="/home" class="dropdown-item my-4">
        <img src="../assets/fork.png" alt="" />
      </router-link>
      <router-link to="/history" class="dropdown-item my-4">
        <img src="../assets/clipboard.png" alt="" />
      </router-link>
      <div  v-if="role == 'admin'" class="dropdown-item my-4">
        <router-link to="/products">
          <img src="../assets/add.png" alt="" />
        </router-link>
      </div>
      <!-- <router-link to="/products" class="dropdown-item my-4">
        <img src="../assets/profil.png" alt="" />
      </router-link> -->
      <router-link to="/" class="dropdown-item my-4">
        <img src="../assets/exit.png" alt="" @click="exit()" />
      </router-link>
    </div>
  </nav>
</template>

<script>
export default {
  name: "navbar",
  data(){
    return{
      cacheKey: 'token',
      roleKey: 'role',
      userKey: 'name',
      role: '',
    }
  },
  methods:{
    exit(){
      localStorage.setItem(this.cacheKey, '');
      localStorage.setItem(this.roleKey, '');
      localStorage.setItem(this.userKey, '');
    },
  },
  mounted(){
    this.role = localStorage.getItem(this.roleKey)
  }
};
</script>

<style scoped>
.dropdown-menu {
  min-width: 4rem;
  margin: 1.5rem 0 0;
}

.dropdown-item {
  padding: 0;
}
</style>
