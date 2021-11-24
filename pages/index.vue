<template>
  <div>
    <select v-model="$colorMode.preference">
      <option value="system">System</option>
      <option value="light">Light</option>
      <option value="dark">Dark</option>
      <option value="sepia">Sepia</option>
    </select>
    <div class="flex justify-center">
      <div class="bg-gray-300 dark:bg-gray-800 w-full lg:w-7/12 rounded-lg lg:rounded-l-none">
        <h3 class="pt-4 text-center text-2xl font-semibold">SEND EMBED</h3>
        <form @submit="submit" class="px-8 pt-6 pb-8 mb-4 rounded">
          <div class="mb-4">
            <label class="block mb-2 text-sm font-bold" for="token">Token</label>
            <input autocomplete="off" v-model="token" class="dark:text-white dark:bg-gray-700 border-none w-full px-3 py-2 mb-3 leading-tight border rounded .shadow-2xl appearance-none focus:outline-none focus:ring transition" type="text" id="token" placeholder="token">
          </div>
          <div class="mb-4">
            <label class="block mb-2 text-sm font-bold" for="channel">Channel id</label>
            <input autocomplete="off" v-model="channelid" class="dark:text-white dark:bg-gray-700 border-none w-full px-3 py-2 mb-3 leading-tight border rounded .shadow-2xl appearance-none focus:outline-none focus:ring transition" type="text" id="channel" placeholder="Channel_id">
          </div>
          <div class="mb-4">
            <label class="block mb-2 text-sm font-bold" for="title">Title</label>
            <input autocomplete="off" v-model="title" class="dark:text-white dark:bg-gray-700 border-none w-full px-3 py-2 mb-3 leading-tight border rounded .shadow-2xl appearance-none focus:outline-none focus:ring transition" type="text" id="title" placeholder="Title">
          </div>
          <div class="mb-4">
            <label class="block mb-2 text-sm font-bold" for="description">Description</label>
            <textarea rows="5" v-model="description" class="dark:text-white dark:bg-gray-700 border-none w-full px-3 py-2 mb-3 leading-tight border rounded .shadow-2xl appearance-none focus:outline-none focus:ring transition" type="text" id="description" placeholder="Description"></textarea>
          </div>
          <div class="mb-4">
            <label class="block mb-2 text-sm font-bold" for="thumbnail">Thumbnail</label>
            <input autocomplete="off" v-model="thumbnail" class="dark:text-white dark:bg-gray-700 border-none w-full px-3 py-2 mb-3 leading-tight border rounded .shadow-2xl appearance-none focus:outline-none focus:ring transition" type="url" id="thumbnail" placeholder="Thumbnail">
          </div>
          <div class="mb-4">
            <label class="block mb-2 text-sm font-bold" for="color">Color</label>
            <input autocomplete="off" v-model="color" class="dark:text-white dark:bg-gray-700 border-none w-full py-1 px-1 mb-3 leading-tight border rounded .shadow-2xl appearance-none focus:outline-none focus:ring transition" type="color" id="color" value="#ff0000" placeholder="Color">
          </div>
          <div>
            <p class="mb-4">{{message}}</p>
            <button type="submit" class="w-full py-2 px-4 text-white bg-blue-500 hover:bg-blue-700 transition rounded focus:outline-none focus:ring">Submit</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data:() => {
    return {
      token:'',
      title: '',
      description: '',
      channelid: '',
      thumbnail: '',
      message: '',
      color: '#ff0000'
    }
  },
  methods: {
    HEXToVBColor: function(rrggbb) {
      var bbggrr = rrggbb.substr(4, 2) + rrggbb.substr(2, 2) + rrggbb.substr(0, 2);
      return parseInt(bbggrr, 16);
    },
    submit: function(e) {
      e.preventDefault();
      let colorint = this.HEXToVBColor(this.color);
      var date = new Date();
      let timestamps = date.toISOString();
      this.$axios.post(`https://discord.com/api/v9/channels/${this.channelid}/messages`,{embeds:[{title:this.title,description:this.description,image:{url:this.thumbnail},timestamp:timestamps,author:{name:'Emrah#9891',icon_url:'https://cdn.discordapp.com/avatars/441221465019514881/9006dbe5c31c1159ff0fd16c2e3bd28a.png?size=100'},footer:{text:'Emrah#9891',icon_url:'https://cdn.discordapp.com/avatars/441221465019514881/9006dbe5c31c1159ff0fd16c2e3bd28a.png?size=100'},color:colorint}]},{headers:{'Content-Type':'application/json','authorization':this.token}}).then(() => {
        this.message = "Success!"
      }).catch((e) => {
        console.log(e);
        this.message = e;
      })
    }
  }
};
</script>
