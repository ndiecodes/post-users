<template>
  <div >
      <div class="container mx-auto px-1">
          <div v-for="user in users" :key="user.id" class="border m-6 rounded-lg  bg-white mx-auto max-w-lg shadow-lg rounded-lg overflow-hidden">
            	<div class="sm:flex sm:items-center px-6 py-4">
                	<img class="block h-16 sm:h-24 rounded-full mx-auto mb-4 sm:mb-0 sm:mr-4 sm:ml-0" src="https://api.adorable.io/avatars/196/abott@adorable.png" alt="">
               		<div class="text-center sm:text-left sm:flex-grow">
                    	 <div class="mb-4">
                        	<p class="text-xl font-bold leading-tight text-indigo-600">{{user.name}}</p>
                           <p class="text-sm leading-tight text-grey-dark pt-1">{{user.email}}</p>
                           <p class="text-sm leading-tight text-grey-dark pt-1">{{user.company.catchPhrase}}</p>
                       	</div>
                        <div class="ext-center md:text-left lg:text-left">
                       
                        	<button class="text-xs font-semibold rounded px-6 py-1 leading-normal bg-white border border-purple text-purple hover:bg-indigo-600 hover:text-white">See Posts</button>
                     	  </div>
				        	</div>
              </div>
          </div>
      </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import axios from "axios"
export default {
  name: "home",
  components: {
    HelloWorld
  },
  data: function () {
    return {
      users: []
    }
  },
  mounted: function () {
    this.loadUsers()
  },
  methods: {
    loadUsers: function() {
      axios.get('https://jsonplaceholder.typicode.com/users/')
      .then(response => {
       this.users = response.data
      })
      .catch(err => {
        console.log(err)
        
      })
    }
  }

};
</script>
