<template>
  <div class="container-fluid">
    <div>Text: {{ nnn }}</div>
    <div>Count: {{ bendcount }}</div>
    <div>狀態: {{ status }}</div>
    <div class="form-inline" style="display: flex">
      <input
        type="text"
        class="form-control"
        style="width: 180px; margin-right: 10px"
        v-model="username"
      />
      <button class="btn btn-primary" @click="updateUsername">更新姓名</button>
      <select
        name=""
        id=""
        class="form-control"
        v-model="nbaName"
        @change="changenba"
      >
        <option value="james">james</option>
        <option value="melon">melon</option>
      </select>

      <select
        name=""
        id=""
        class="form-control"
        v-model="banknum"
        @change="changebanknum"
      >
        <option value="001">001</option>
        <option value="002">002</option>
      </select>
    </div>
    <table class="table table-striped mt-5">
      <thead>
        <tr>
          <th>#</th>
          <th>Img</th>
          <th>Name</th>
          <th>Email</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="(data, index) in listData"
          :key="data.id"
          :class="{ 'bg-info': data.selected }"
        >
          <td>{{ index + 1 }}</td>
          <td><img :src="data.picture.medium" alt="" style="width: 50px" /></td>
          <td>{{ data.name.first }} {{ data.name.last }}</td>
          <td>{{ data.email }}</td>
          <td>
            <button class="btn btn-outline-primary" @click="clickMe(data)">
              點我
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "List",
  props: ["status", "bendcount", "nnn"],
  data() {
    return {
      msg: "welcome to your vue.js app",
      listData: [],
      username: "Casper",
      nbaName: "melon",
      banknum: "001",
    };
  },
  methods: {
    getList() {
      fetch("https://randomuser.me/api/?results=25").then((response) =>
        response.json().then((data) => {
          console.log(data);
          this.listData = data.results;
        })
      );
    },
    updateUsername() {
      let vm = this;
      vm.$emit("pushNewName", vm.username);
    },
    clickMe(i) {
      i.selected = !i.selected;
      console.log(i.selected);
    },
    changenba() {
      let vm = this;
      vm.$emit("newnba", vm.nbaName);
    },
    changebanknum() {
      let vm = this;
      vm.$emit("setbanknum", vm.banknum);
    },
  },
  mounted() {
    this.getList();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
