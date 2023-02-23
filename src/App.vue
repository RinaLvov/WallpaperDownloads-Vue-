<template>
  <div id="app">
    <nav>
      <router-link to="/"></router-link>
    </nav>
    <router-view />
  </div>
</template>

<style>
p {
  text-align: center;
  font-family: "Montserrat", sans-serif;
  margin-top: 5px;
}

.wallpapers {
  display: flex;
  justify-content: space-between;
  margin-top: 100px;
  flex-wrap: wrap;
}

.wallpapers a {
  background-color: #bbcacb;
}

img {
  height: 170px;
  width: 280px;
  margin: 2px;
}

.image {
  padding: 10px;
}

a {
  margin-left: 130px;
  color: rgb(64, 62, 62);
  padding: 9px 25px;
  border-radius: 50px;
}

.downloadButton {
  margin-top: 15px;
  border: none;
  background-color: #bbcacb;
  cursor: pointer;
  transition: all 0.3s ease 0s;
  display: flex;
  justify-content: center;
}

a:hover {
  background-color: #909999;
  cursor: pointer;
}

.downloadButton:hover {
  background-color: #909999;
  cursor: pointer;
}
</style>
