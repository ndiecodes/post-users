<template>
  <div class="container max-w-xl mx-auto px-2">
      <div id="nav">
        <router-link :to="{ name: 'home'}">
            <h3 class="text-xl text-indigo-600 font-extrabold text-center logo-text p-5">
            Home
        </h3> </router-link>
    </div>

    <div class="pb-10 pt-2">
      <div class="mb-4">
        <p class="text-xl font-bold leading-tight text-left ">
           {{ post.title | capitalize }}
        </p>

        <p class="text-sm text-left leading-tight text-grey-dark pt-2 pb-2">
         {{ post.body | capitalize }}
        </p>

        <p class="mt-2"><b>Posted By: </b> {{user.name}}</p>
        <hr class="mt-1 mb-2" />
      </div>

      <Comments :postId="1" />

    </div>
  </div>
</template>

<script>
import Comments from "@/components/Comments";
import axios from "axios";
export default {
  name: "post",
  components: {
    Comments
  },
  data: function() {
    return {
      post: {},
      user: {}
    };
  },
  mounted: function() {
    this.loadPost()
  },

  methods: {
    loadPost: function() {
    let self = this;
      axios
        .get(
          `https://jsonplaceholder.typicode.com/posts/${this.$route.params.postId}`
        )
        .then(response => {
          this.post = response.data;
          self.loadUser();
        })
        .catch(err => {
          console.log(err);
        });
    },

    loadUser: function() {
      axios
        .get(
          `https://jsonplaceholder.typicode.com/users/${this.post.userId}`
        )
        .then(response => {
          this.user = response.data;
          console.log(this.user)
        })
        .catch(err => {
          console.log(err);
        });
    },
  },


  filters: {
    capitalize: function(value) {
      if (!value) return "";
      value = value.toString();
      return value.charAt(0).toUpperCase() + value.slice(1);
    }
  }
};
</script>
