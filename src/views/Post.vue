<template>
  <div>
    <div id="nav">
      <h1 class="text-2xl text-indigo-600 font-extrabold logo-text p-5"></h1>
    </div>

    <div class="container max-w-xl mx-auto px-1 pb-10">
      <div class="mb-4">
        <p class="text-xl font-bold leading-tight text-left ">
          sunt aut facere repellat provident occaecati excepturi optio
          reprehenderit
        </p>

        <p class="text-sm text-left leading-tight text-grey-dark pt-2 pb-2">
          quia et suscipit\nsuscipit recusandae consequuntur expedita et
          cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem
          sunt rem eveniet architecto
        </p>
        <hr class="mt-5 mb-2" />
      </div>

      <Comments :postId="1" />

      <div>
        <div class="flex items-center">
          <img
            class="block h-5 rounded-full mr-4"
            src="https://api.adorable.io/avatars/196/abott@adorable.png"
            alt=""
          />

          <p class="text-sm font-bold leading-tight ">Eliseo@gardner.biz</p>
        </div>
        <p class="text-left py-2">
          laudantium enim quasi est quidem magnam voluptate ipsam eos\ntempora
          quo necessitatibus\ndolor quam autem quasi\nreiciendis et nam sapiente
          accusantium
        </p>
      </div>
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
      posts: []
    };
  },
  mounted: function() {
    // this.loadComments()
  },

  methods: {
    loadComments: function() {
      axios
        .get(
          `https://jsonplaceholder.typicode.com/users/${this.$route.params.userId}/posts/`
        )
        .then(response => {
          this.posts = response.data;
        })
        .catch(err => {
          console.log(err);
        });
    }
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
