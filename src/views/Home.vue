<template>
  <div class="homepage">
    <div class="container-box">
      <navbar/>
      <div class="inner-container">
        <div class="sidebar">
          <div class="side-navbar-link" v-for="(link, index) in links" :key="index">
            <div class="icon">
              <v-icon :class="`${link.status}`">{{link.icon}}</v-icon>
            </div>
            <div class="link-name">
              <a href :class="`${link.status}`">{{link.name}}</a>
            </div>
          </div>
        </div>
        <div class="main">
          <div class="row">
            <div class="col-12">
              <h1 class="heading">History of movies</h1>
            </div>
          </div>
          <div class="search-row">
            <div class="row">
              <div class="col-8">
                <div class="title-description">EHU | Instructor:Keira Knightley</div>
              </div>
              <div class="col-4">
                <div class="search-box">
                  <input type="text" placeholder="Find">
                  <v-icon>search</v-icon>
                </div>
              </div>
            </div>
          </div>
          <div class="add-post">
            <div class="row">
              <div class="col-12">
                <div class="most-recent">
                  <button class="active1">Most Recent</button>
                  <button>Most Boosted</button>
                </div>
              </div>
            </div>
            <div class="row">
              <div class="col-12">
                <div class="greet-user">Hi,User!</div>
              </div>
            </div>
            <div class="row">
              <div class="col-7">
                <Addpost/>
              </div>
              <div class="col-5">
                <calendar/>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import navbar from "../components/navbar";
import Addpost from "../components/AddPost";
import Calendar from "../components/Calendar";
export default {
  name: "Home",
  components: {
    navbar,
    Addpost,
    Calendar
  },
  data() {
    return {
      links: [
        { name: "Discussion", icon: "message" ,status:"active"},
        { name: "Classmates", icon: "people" ,status:"inactive"},
        { name: "Library", icon: "library_books" ,status:"inactive"},
        { name: "Profile", icon: "settings" ,status:"inactive"}
      ]
    };
  }
};
</script>

<style scoped>
.inner-container {
  background-color: #f3f3f3;
  width: 100%;
  height: 100%;
  border: 1px solid #ededed;
  display: flex;
}
.sidebar {
  width: 120px;
  height: 600px;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-top: 87px;
}
.main {
  flex-basis: 966px;
  padding: 15px 0px;
}
.side-navbar-link {
  margin-top: 20px;
}

.icon {
  text-align: center;
}
.link-name a {
  text-align: center;
  text-decoration: none;
  color: #95a5a6;
  cursor: pointer;
}
.search-row {
  width: 100%;
  margin-top: 5px;
}
.main .heading {
  font-size: 18px;
  color: black;
  font-weight: 500;
}
.search-row .title-description {
  color: #95a5a6;
}
.search-box {
  display: flex;
  justify-content: flex-end;
}
.search-box input {
  border: 1px solid #95a5a67d;
  box-shadow: inset 1px 2px 8px rgba(0, 0, 0, 0.07);
  background-color: #fff;
  padding: 4px 5px;
  width: 254px;
  border-radius: 3px;
  outline: 0;
}
.search-box .v-icon {
  margin-left: -20px;
  font-size: 20px;
}
.add-post {
  width: 100%;
  margin-top: 20px;
  background-color: #f5f6fa;
  border: 1px solid #ededed;
  padding: 20px;
}
.most-recent button {
  padding: 4px 8px;
  border: 1px solid #95a5a67d;
  border-radius: 1px;
  outline: 0;
}
.greet-user {
  color: green;
  text-align: right;
}
.active{
  color: greenyellow !important;
}
.active1 {
  background-color: #ededed;
}
@media screen and (max-width: 600px) {
  .search-box{
    display: flex;
    justify-content: flex-start;
    margin-top: 5px; 
  }
}
</style>
