<template>
  <div class="bg-white relative overflow-hidden h-screen bg-gray-100">

    <form
      class="flex flex-col md:flex-row w-3/4 md:w-full max-w-sm md:space-x-3 space-y-3 md:space-y-0 justify-items-center mx-auto mt-20">
      <div class=" relative m-auto">
        <input v-model="search" type="text" id="&quot;form-subscribe-Subscribe"
          class=" rounded-lg border-transparent flex-1 appearance-none border border-gray-300 w-full py-2 px-4 bg-white text-gray-700 placeholder-gray-400 shadow-sm text-base focus:outline-none focus:ring-2 focus:ring-blue-600 focus:border-transparent"
          placeholder="Cari Folder" />
      </div>

      <div class="relative inline-block text-left">
        <div>
          <button type="button" @click="openKategori"
            class=" border border-gray-300 bg-white dark:bg-gray-800 shadow-sm flex items-center justify-center w-full rounded-md  px-4 py-2 text-sm font-medium text-gray-700 dark:text-gray-50 hover:bg-gray-50 dark:hover:bg-gray-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-gray-500"
            id="options-menu">
            {{ kategori ? kategori : "Kategori" }}
            <svg width="20" height="20" fill="currentColor" viewBox="0 0 1792 1792" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M1408 704q0 26-19 45l-448 448q-19 19-45 19t-45-19l-448-448q-19-19-19-45t19-45 45-19h896q26 0 45 19t19 45z">
              </path>
            </svg>
          </button>
        </div>

        <div
          class="origin-top-right absolute right-0 mt-2 w-56 rounded-md shadow-lg bg-white dark:bg-gray-800 ring-1 ring-black ring-opacity-5 "
          :class="{'hidden':!active}">
          <div class="py-1 " role="menu" aria-orientation="vertical" aria-labelledby="options-menu">
            <a href="#" @click.prevent="filterCategory('')"
              class="block block px-4 text-md text-gray-700 hover:bg-gray-100 hover:text-gray-900 dark:text-gray-100 dark:hover:text-white dark:hover:bg-gray-600"
              role="menuitem">
              <span class="flex flex-col">
                <span>
                  Semua
                </span>
              </span>
            </a>
            <a href="#" @click.prevent="filterCategory('bendahara')"
              class="block block px-4  text-md text-gray-700 hover:bg-gray-100 hover:text-gray-900 dark:text-gray-100 dark:hover:text-white dark:hover:bg-gray-600"
              role="menuitem">
              <span class="flex flex-col">
                <span>
                  Bendahara
                </span>
              </span>
            </a>
            <a href="#" @click.prevent="filterCategory('keuangan')"
              class="block block px-4  text-md text-gray-700 hover:bg-gray-100 hover:text-gray-900 dark:text-gray-100 dark:hover:text-white dark:hover:bg-gray-600"
              role="menuitem">
              <span class="flex flex-col">
                <span>
                  Keuangan
                </span>
              </span>
            </a>
            <a href="#" @click.prevent="filterCategory('sakip')"
              class="block block px-4  text-md text-gray-700 hover:bg-gray-100 hover:text-gray-900 dark:text-gray-100 dark:hover:text-white dark:hover:bg-gray-600"
              role="menuitem">
              <span class="flex flex-col">
                <span>
                  Sakip
                </span>
              </span>
            </a>
            <a href="#" @click.prevent="filterCategory('perjadin')"
              class="block block px-4  text-md text-gray-700 hover:bg-gray-100 hover:text-gray-900 dark:text-gray-100 dark:hover:text-white dark:hover:bg-gray-600"
              role="menuitem">
              <span class="flex flex-col">
                <span>
                  Perjadin
                </span>
              </span>
            </a>
            <a href="#" @click.prevent="filterCategory('surat')"
              class="block block px-4  text-md text-gray-700 hover:bg-gray-100 hover:text-gray-900 dark:text-gray-100 dark:hover:text-white dark:hover:bg-gray-600"
              role="menuitem">
              <span class="flex flex-col">
                <span>
                  Surat
                </span>
              </span>
            </a>
            <a href="#" @click.prevent="filterCategory('sop')"
              class="block block px-4  text-md text-gray-700 hover:bg-gray-100 hover:text-gray-900 dark:text-gray-100 dark:hover:text-white dark:hover:bg-gray-600"
              role="menuitem">
              <span class="flex flex-col">
                <span>
                  SOP
                </span>
              </span>
            </a>
            <a href="#" @click.prevent="filterCategory('kepegawaian')"
              class="block block px-4  text-md text-gray-700 hover:bg-gray-100 hover:text-gray-900 dark:text-gray-100 dark:hover:text-white dark:hover:bg-gray-600"
              role="menuitem">
              <span class="flex flex-col">
                <span>
                  kepegawaian
                </span>
              </span>
            </a>
          </div>
        </div>
      </div>
<button @click.prevent="resetFolders" class="bg-gray-300 hover:bg-gray-400 text-gray-800  py-1 px-6 rounded inline-flex items-center">

  <span class="text-xs" > Reset</span>
</button>

    </form>

    <br>
    <br>
    <br>
    <div class="flex w-full justify-items-center ">

      <div class="flex flex-wrap -m-2 p-5" v-if="search || kategori">
        <div class="p-2 lg:w-1/4 md:w-1/2 w-full px-5 px-2 " v-for="folder in filteredFolders" :key="folder">
          <div class="flex items-center  p-4 rounded-lg bg-white shadow-sm ">

            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10" viewBox="0 0 20 20" fill="currentColor">
              <path d="M2 6a2 2 0 012-2h5l2 2h5a2 2 0 012 2v6a2 2 0 01-2 2H4a2 2 0 01-2-2V6z" />
            </svg>


            <div class="flex-grow">
              <a :href="folder.url" target="_blank" class="text-gray-700 text-lg font-semibold hover:text-blue-500"> {{ folder.name }}</a>

            </div>
          </div>
        </div>

      </div>
      <div class="flex flex-wrap -m-2 p-5" v-else>
        <div class="p-2 lg:w-1/4 md:w-1/2 w-full px-5 px-2 " v-for="folder in folders" :key="folder">
          <div class="flex items-center  p-4 rounded-lg bg-white shadow-sm ">

            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10" viewBox="0 0 20 20" fill="currentColor">
              <path d="M2 6a2 2 0 012-2h5l2 2h5a2 2 0 012 2v6a2 2 0 01-2 2H4a2 2 0 01-2-2V6z" />
            </svg>


            <div class="flex-grow">
              <a :href="folder.url" target="_blank" class="text-gray-700 text-lg font-semibold hover:text-blue-500"> {{ folder.name }}</a>

            </div>
          </div>
        </div>
      </div>
    </div>




  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      kategori:'',
      active:false,
      search:'',
      filtered_folder:'',
      folders:[{
        name:'LPJ',
        url:'https://drive.google.com/drive/folders/1I0-ZNAX-hst9uWaucTexNLC0xRQDy4pr?usp=sharing',
        img:'',
        group:'bendahara'
      },{
        name:'SP2D',
        url:'https://drive.google.com/drive/folders/1CrwoXLDFmS8HGKcro2dSCBQzeA8ZtHJG?usp=sharing',
        img:'',
        group:'bendahara'
      },{
        name:'SPJ',
        url:'https://drive.google.com/drive/folders/1ql_ZhCbs7xrTlcHkLrRmN0wDgRnoOL1w?usp=sharing',
        img:'',
        group:'bendahara'
      },{
        name:'SPM',
        url:'https://drive.google.com/drive/folders/16olhI5JLwIYrtPZi2nPNsHpQqoSUOrFt?usp=sharing',
        img:'',
        group:'bendahara'
      },
      {
        name:'Renstra',
        url:'https://drive.google.com/drive/folders/1wRXGWZjRpZEvSuDHCQCkdMPdl0VO4xfX?usp=sharing',
        img:'',
        group:'sakip'
      },{
        name:'IKU',
        url:'https://drive.google.com/drive/folders/14zq6lQdjm3yrBFuU4kIqTMG_70BQnz7i?usp=sharing',
        img:'',
        group:'sakip'
      },
            {
        name:'IKI',
        url:'https://drive.google.com/drive/folders/1DmVE-25aeLoYF04iHa-vy7ouzFHhYB8b?usp=sharing',
        img:'',
        group:'sakip'
      },{
        name:'LKIN',
        url:'https://drive.google.com/drive/folders/1wRXGWZjRpZEvSuDHCQCkdMPdl0VO4xfX?usp=sharing',
        img:'',
        group:'sakip'
      },
            {
        name:'FRA',
        url:'https://drive.google.com/drive/folders/1yMeqiiHC--TkGxVzl-k3zZ-c7dJ82QpE?usp=sharing',
        img:'',
        group:'sakip'
      },
            {
        name:'PK',
        url:'https://drive.google.com/drive/folders/1BsoyNGonDE18U1f-WEg7jUcxDuA80viX?usp=sharing',
        img:'',
        group:'sakip'
      },
                  {
        name:'Laporan Keuangan',
        url:'https://drive.google.com/drive/folders/13zxUaJ0E9OZYm0QeKMsrRqA_TH8ld8b_?usp=sharing',
        img:'',
        group:'keuangan'
      },
                  {
        name:'Laporan Perjadin',
        url:'',
        img:'',
        group:'perjadin'
      },
            {
        name:'SPD',
        url:'https://drive.google.com/drive/folders/1pypBUl1vJ6EmQqOanQ_jG4Z6zrZkDabq?usp=sharing',
        img:'',
        group:'perjadin'
      },
                  {
        name:'Surat Tugas',
        url:'https://drive.google.com/drive/folders/1GBDVNXOT5a8pLcIp8B5X1B6WXYgVgmAz?usp=sharing',
        img:'',
        group:'perjadin'
      },
                  {
        name:'Surat Masuk',
        url:'https://drive.google.com/drive/folders/1Yz6SEN4hvucLqx943KOebdg_ZHqPuTHM?usp=sharing',
        img:'',
        group:'surat'
      },
                        {
        name:'Surat Keluar',
        url:'https://drive.google.com/drive/folders/1t2GBZF4KFtTTeK5DOVFM9sk33RvorCyR?usp=sharing',
        img:'',
        group:'surat'
      },
                        {
        name:'Dokumen Lelang',
        url:'https://drive.google.com/drive/folders/1mDFpD-hAyvL-MgHnKBQFfxpj0sezIdiZ?usp=sharing',
        img:'',
        group:'surat'
      },
                        {
        name:'Lainnya',
        url:'https://drive.google.com/drive/folders/1esA1XCIycdfXkDs23IiYxBNvR7QLi0rI?usp=sharing',
        img:'',
        group:'surat'
      },
                              {
        name:'SOP',
        url:'',
        img:'',
        group:'sop'
      },
       {
        name:'Data Pegawaian',
        url:'',
        img:'',
        group:'kepegawaian'
      },



      ]
    }
  },
  computed:{
    filteredFolders(){
      return this.folders.filter(folder=>{

        if(this.search !=null && this.kategori !=''){
          return folder.name.indexOf(this.search) > -1 && folder.group == this.kategori
        }else if(this.kategori !=''){
         return folder.group == this.kategori
        }
       else if(this.search != null){
          return folder.name.indexOf(this.search) > -1
        }

      }

      )
    }
  },
  methods:{
    filterCategory(kategori){
      this.active= !this.active
      return this.kategori =kategori
    },
    openKategori(){
      this.active= !this.active
    },
    resetFolders(){
      this.kategori='',
      this.active=false,
      this.search=null
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}

</style>
