<template>
  <div >

    <div id="nav">
      <h1 class="text-2xl text-indigo-600 font-extrabold logo-text p-5">Posts </h1>
    </div>
    
      <div class="container mx-auto px-1 pb-10">
          <div v-for="post in posts" :key="post.id" class="border m-6 rounded-lg  bg-white mx-auto max-w-xl shadow-lg rounded-lg overflow-hidden">
               		<div class="text-center sm:text-left sm:flex-grow px-6 py-4">
                    	 <div class="mb-4">
                        	<p class="text-xl font-bold leading-tight ">{{post.title | capitalize}}</p>
           
                           <p class="text-sm leading-tight text-grey-dark pt-2 pb-2">{{post.body | capitalize}}</p>
                       	</div>
                        <div class="ext-center md:text-left lg:text-left">
                       
                        	<button class="text-xs font-semibold rounded px-6 py-1 leading-normal bg-white border border-purple text-purple hover:bg-indigo-600 hover:text-white">Read More >></button>
                     	  </div>
				        	</div>
         </div>
      </div>
  </div>
</template>

<script>
import axios from "axios"
export default {
  name: "posts",
  data: function () {
    return {
      posts: []
    }
  },
  mounted: function () {
    this.loadUserPosts()
  },

  methods: {
   
    loadUserPosts: function() {
      axios.get(`https://jsonplaceholder.typicode.com/users/${this.$route.params.userId}/posts/`)
      .then(response => {
       this.posts = response.data
      })
      .catch(err => {
        console.log(err)
        
      })
    }
  },

  filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
  }


};
</script>
