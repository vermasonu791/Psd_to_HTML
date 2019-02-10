<template>
  <div class="row">
    <div class="col-12">
      <nav class="navbar">
        <div class="icon">
          <img src="../assets/icon.png" alt>
        </div>
        <div class="spacer"></div>
        
        <div class="link" v-for="(link ,index) in navlink" :key="index">
            <div class="links"><span class="vertical-line"></span>{{link}}</div>
        </div>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  name: "navbar",
  data() {
    return {
      navlink: ["Courses", "Calendar", "Help", "Me"]
    };
  }
};
</script>

<style scoped>
.navbar {
  width: 100%;
  background-color: #fff;
  box-shadow: 0px 2px #c8cfcf;
  display: flex;
  align-items: center;
  padding: 10px 120px;
}
.icon img {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  cursor: pointer;
}
.link .links{
  text-decoration: none;
  color: #34495e;
  font-size: 16px;
  cursor: pointer;
}
.vertical-line {
  border-left: 2px solid rgb(179, 190, 179);
  height: 20px;
  margin: 0px 8px;
}
.link .links {
  height: 100%;
}
@media screen and (max-width: 768px) {
 .navbar {

  padding: 10px 0px;
}
}
</style>
