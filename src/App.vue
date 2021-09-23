<template>
  <div id="nav">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Navbar</a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Link</a>
            </li>
            <li class="nav-item dropdown">
              <a
                class="nav-link dropdown-toggle"
                href="#"
                id="navbarDropdown"
                role="button"
                data-bs-toggle="dropdown"
                aria-expanded="false"
              >
                Dropdown
              </a>
              <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
                <li><a class="dropdown-item" href="#">Action</a></li>
                <li><a class="dropdown-item" href="#">Another action</a></li>
                <li><hr class="dropdown-divider" /></li>
                <li>
                  <a class="dropdown-item" href="#">Something else here</a>
                </li>
              </ul>
            </li>
            <li class="nav-item">
              <a class="nav-link disabled">Disabled</a>
            </li>
          </ul>
          <div class="form-inline mr-3">
            <input
              class="form-control"
              type="text"
              placeholder="someting..."
              v-model="mytext"
            />
            <button class="form-control" @click="this.mycount += 1">
              count
            </button>
            <select
              name=""
              id=""
              class="form-control"
              @change="changeStatus"
              v-model="status"
            >
              <option value="線上">線上</option>
              <option value="線下">線下</option>
            </select>
            Hi, {{ username }} {{ mynbaName }}{{ mybanknum }}
          </div>
        </div>
      </div>
    </nav>

    <router-view
      :status="myStatus"
      :bendcount="mycount"
      :nnn="mytext"
      @pushNewName="getNewName"
      @newnba="getnabname"
      @setbanknum="getmybanknum"
    ></router-view>
  </div>
  <router-view />
</template>

<style lang="scss"></style>

<script>
export default {
  name: "app",
  data() {
    return {
      status: "線上",
      myStatus: "線上",
      username: "",
      mycount: 0,
      // bendcount: 0,
      mytext: "",
      mynbaName: "melon",
      mybanknum: "001",
    };
  },
  methods: {
    changeStatus() {
      this.myStatus = this.status;
    },
    getNewName(newname) {
      let vm = this;
      vm.username = newname;
    },
    addCount() {
      this.mycount += 1;
      // this.bendcount = this.mycount;
    },
    getnabname(name) {
      let vm = this;
      vm.mynbaName = name;
    },
    getmybanknum(num) {
      this.mybanknum = num;
    },
  },
};
</script>

