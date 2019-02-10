<template>
  <div class="post-area">
    <div class="add-data">
      <img src="../assets/person.jpeg" class="person-img" alt="alt" width="40" height="40">&nbsp;
      <div class="textarea">
        <textarea name="text" v-model="postdata"></textarea>
        <div class="upload">
          <v-icon>attachment</v-icon>
          <!-- <button>Upload</button> -->
          <label class="custom-file-upload">
            <input type="file" @change="uploadImg" style="outline:0">
            Upload
          </label>
          <div class="spacer"></div>
          <button id="post-button" @click="addPost" style="outline:0">Post</button>
        </div>
      </div>
    </div>
    <div class="view-post" v-for="(post,index) in post" :key="index">
      <br>
      <img src="../assets/person.jpeg" class="person-img" alt="alt" width="40" height="40">&nbsp;
      <div class="view-img">
        <div class="user-info">
          <div class="user-name">Keira</div>
          <div class="movie-name">{{post.name}}</div>
          <div class="movie-img">
            <img :src="post.image" alt>
          </div>
          <div class="upload-time">{{post.time}}</div>
        </div>
        <div class="share-button">
          <v-icon>arrow_upward</v-icon>
          <a href>Boost</a>
          <v-icon>share</v-icon>
          <a href>Share</a>
          <v-icon>zoom_in</v-icon>
          <a href>Zoom</a>
        </div>
        <div class="show-comment" v-for="(comment,index) in post.comments" :key="index">
          <div class="comment-person">
            <img src="../assets/person.jpeg" alt width="40" height="40"> &nbsp;
          </div>
          <div class="comment-content">{{comment}}</div>
        </div>
        <div class="comment-box">
          <img src="../assets/person.jpeg" alt="alt" width="40" height="40">&nbsp;
          <input type="text" placeholder="Write a comment" v-model="post.dummyComment">
          <button @click="postComment(post)">
            <v-icon>arrow_upward</v-icon>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddPost",
  data() {
    return {
      post: [
        {
          name: "Anna karemla movie 2012",
          image:
            "https://st1.bollywoodlife.com/wp-content/uploads/2011/11/Rockstar-review.jpg",
          time: "4:12 PM",
          comments: ["Nice Movie"],
          dummyComment: " "
        }
      ],
      imageurl: "",
      postdata: "",
      uploadTime: null
    };
  },
  methods: {
    //Add Post
    addPost() {
      console.log(this.postdata);
      if (this.postdata === "" || this.postdata === null) {
        this.$swal({
          type: "error",
          title: "Oops...",
          text: "You cannot add empty comment"
        });
      } else {
        let date = new Date();
        let options = {
          hour: "2-digit",
          minute: "2-digit"
        };
        this.uploadTime = date.toLocaleTimeString("en-us", options);
        this.post.push({
          name: this.postdata,
          image: this.imageurl,
          time: this.uploadTime,
          comments: []
        });
        this.$swal("Post Added Successfully");
      }
    },
    //Uload image
    uploadImg() {
      const reader = new FileReader();
      reader.onload = e => {
        this.imageurl = e.target.result;
      };
      reader.readAsDataURL(event.target.files && event.target.files[0]);
      this.$swal("file Uploaded");
    },
    postComment(post) {
      console.log(post.dummyComment);
      if (post.dummyComment === " " || post.dummyComment === null) {
        this.$swal({
          type: "error",
          title: "Oops...",
          text: "You cannot add empty comment "
        });
      } else {
        post.comments.push(post.dummyComment);
        post.dummyComment = null;
      }
    }
  }
};
</script>

<style>
.post-area {
  width: 100%;
  padding: 10px;
  display: flex;
  flex-direction: column;
}

.add-data,
.view-post {
  display: flex;
}
.person-img {
  border: 1px solid #ededed;
  padding: 2px;
}
.view-post {
  margin-top: 20px;
}
.textarea,
.view-img {
  width: 100%;
  border: 1px solid #ededed;
}
.view-img {
  background-color: #fff;
}
.textarea textarea {
  width: 100%;
  height: 100px;
  background-color: #fff;
  outline: 0;
  padding: 8px;
}
.upload {
  width: 100%;
  padding: 10px;
  display: flex;
}
.upload #post-button {
  background-color: #1d9a1dba;
  color: #fff;
  padding: 6px 14px;
}
.view-img .movie-img img {
  width: 100%;
  height: 250px;
}
.user-info {
  padding: 8px;
}
.user-info .movie-name,
.upload-time {
  color: #95a5a6;
}
.user-info .user-name {
  font-size: 18px;
  color: black;
  font-weight: 500;
}
.share-button {
  display: flex;
  align-items: flex-start;
  padding: 12px 5px;
  background-color: #f3f3f3;
  border-top: 1px solid #ededed;
}
.share-button a {
  text-decoration: none;
  margin-right: 12px;
  color: #000;
}
.share-button .v-icon {
  font-size: 15px;
}
.comment-box {
  display: flex;
  padding: 5px;
  width: 100%;
  background-color: #f3f3f3;
}
.comment-box img {
  width: 35 !important;
  height: 35 !important;
  border: 1px solid #ededed;
  padding: 2px;
}
.comment-box input {
  border: 1px solid #ededed;
  background-color: #fff;
  padding: 8px 10px;
  outline: 0;
  width: 100%;
}
.custom-file-upload {
  display: inline-block;
  padding: 6px 4px;
  cursor: pointer;
}
.show-comment {
  width: 100%;
  border-top: 1px solid#ededed;
  display: flex;
  padding: 4px;
  background-color: #f3f3f3;
}
input[type="file"] {
  display: none;
}
.upload .v-icon {
  transform: rotate(90deg);
  font-size: 17px;
}
@media only screen and (max-width: 600px) {
  .post-area {
    width: 100%;
  }
}
</style>
