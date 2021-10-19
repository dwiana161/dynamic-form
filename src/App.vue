<template>
<div id="app">
  <div class="container">
<nav class="navbar navbar-light bg-dark">
  <div class="container-fluid">
    <h2 class="title">FORMULIR</h2>
  </div>
</nav>
</div>
<div class="mb-3"></div>
<div class="container">
<div class="col-12">
<form class="row g-3" @submit.prevent="save">
  <div class="col-auto">
    <label for="staticEmail2" class="visually-hidden">Nama</label>
    <input type="text" v-model="nama" class="form-control bg-light" id="staticEmail2" placeholder="masukkan nama">
  </div>
  <div class="col-auto">
    <label for="inputPassword2" class="visually-hidden">Alamat</label>
    <input type="text" v-model="alamat" class="form-control bg-light" id="inputPassword2" placeholder="masukkan alamat">
  </div>
  <div class="col-auto">
    <button type="submit" class="btn btn-dark mb-3">Confirm identity</button>
  </div>
</form>
</div>
<div class="mb-2"></div>
<table class="table table-border">
  <thead>
    <tr>
      <th>Nama</th>
      <th>Alamat</th>
      <th>Aksi</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(dt, index) in dataTabel" :key="index">
      <td>{{dt.nama}}</td>
      <td>{{dt.alamat}}</td>
      <td> <a href="#" @click="hapus(index)">Hapus</a> </td>
    </tr>
  </tbody>
</table>
</div>
</div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return{
      nama: "",
      alamat: "",
      dataTabel: [],
    }
  },
  methods:{
    save() {
      if (this.nama.trim() == '' || this.alamat.trim()== '') {
        return;
      }

      this.dataTabel.push({
        nama:this.nama,
        alamat: this.alamat,
      })

      this.nama="",
      this.alamat="";
    },
    
    hapus(index){
      this.dataTabel.splice(index, 1)
    }
  }
}
</script>

<style>

body {
  background-image: url(./assets/photo-1593642634443-44adaa06623a.jpg);
  background-size: cover;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}

#app{
  min-height: 200px;
  height: min-content;
  padding: 20px;
  border-radius: 15px;
}

.title{
  color: bisque;
  margin-left: auto;
  margin-right: auto;
}

nav{
  border: 3px solid #234668;
  border-radius: 15px;
}

th, td{
  color: aliceblue;
}

button{
  border: 5px solid #234668;
  cursor: pointer;
}

button:hover {
  background-color: #555e7d;
}

button:focus {
  outline: none;
}
</style>
