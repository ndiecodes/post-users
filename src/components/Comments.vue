<template>
  <div>
    <h2 class="font-bold mb-3">- Comments</h2>
    <div
      v-for="comment in comments"
      :key="comment.id"
      class="mb-3 shadow-md py-3 px-2"
    >
      <div class="flex items-center">
        <img
          class="block h-5 rounded-full mr-4"
          src="https://api.adorable.io/avatars/196/abott@adorable.png"
          alt=""
        />

        <p class="text-sm font-bold leading-tight ">Eliseo@gardner.biz</p>
      </div>
      <p class="text-left py-2">
        laudantium enim quasi est quidem magnam voluptate ipsam eos\ntempora quo
        necessitatibus\ndolor quam autem quasi\nreiciendis et nam sapiente
        accusantium
      </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Comments",
  props: {
    postId: Number
  },
  mounted: function() {
    this.loadComments();
  },
  data: function() {
    return {
      comments: []
    };
  },
  methods: {
    loadComments: function() {
      axios
        .get(
          `https://jsonplaceholder.typicode.com/posts/${this.postId}/comments`
        )
        .then(response => {
          this.comments = response.data;
          console.log(response.data);
        })
        .catch(err => {
          console.log(err);
        });
    }
  }
};
</script>
