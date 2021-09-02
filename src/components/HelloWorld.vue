<template>
  <div class="bg-white relative overflow-hidden h-screen bg-gray-50">

    <form class="flex flex-col md:flex-row w-3/4 md:w-full max-w-sm md:space-x-3 space-y-3 md:space-y-0 justify-items-center mx-auto mt-20">
      <div class=" relative m-auto">
        <input v-model="search" type="text" id="&quot;form-subscribe-Subscribe"
          class=" rounded-lg border-transparent flex-1 appearance-none border border-gray-300 w-full py-2 px-4 bg-white text-gray-700 placeholder-gray-400 shadow-sm text-base focus:outline-none focus:ring-2 focus:ring-purple-600 focus:border-transparent"
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

      <button @click.prevent="resetFolders"
        class="flex-shrink-0 px-4 py-2 text-base font-semibold text-white bg-red-600 rounded-lg shadow-md hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-red-500 focus:ring-offset-2 focus:ring-offset-red-200"
        type="reset">
        Reset
      </button>
    </form>

    <br>
<br>
<br>
  <div class="flex w-full justify-items-center ">
    <div class="grid grid-cols-3 m-auto" v-if="search || kategori">
      <div class="" v-for="folder in filteredFolders" :key="folder">


<div class="shadow-lg rounded-xl bg-white w-full md:w-64 p-6 bg-white dark:bg-gray-800 overflow-hidden m-2 mx-auto ">
    <p class="text-gray-800 text-base">
        {{ folder.name }}
    </p>

    <div class="mt-4">
        <button type="button" class="py-2 px-4  bg-blue-700 hover:bg-blue-800 focus:ring-blue-500 focus:ring-offset-blue-200 text-white w-full transition ease-in duration-200 text-center text-base font-semibold shadow-md focus:outline-none focus:ring-2 focus:ring-offset-2 rounded-lg ">
            Buka
        </button>
    </div>
</div>

      </div>

    </div>
    <div class="" v-else>

      {{ folders }}
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
        url:'',
        img:'',
        group:'bendahara'
      },{
        name:'SP2D',
        url:'',
        img:'',
        group:'bendahara'
      },{
        name:'SPJ',
        url:'',
        img:'',
        group:'bendahara'
      },{
        name:'SPM',
        url:'',
        img:'',
        group:'bendahara'
      },
      {
        name:'Renstra',
        url:'',
        img:'',
        group:'sakip'
      },{
        name:'IKU',
        url:'',
        img:'',
        group:'sakip'
      },
            {
        name:'IKI',
        url:'',
        img:'',
        group:'sakip'
      },{
        name:'LKIN',
        url:'',
        img:'',
        group:'sakip'
      },
      {
        name:'LKIN',
        url:'',
        img:'',
        group:'sakip'
      },
            {
        name:'FRA',
        url:'',
        img:'',
        group:'sakip'
      },
            {
        name:'PK',
        url:'',
        img:'',
        group:'sakip'
      },
                  {
        name:'Laporan Keuangan',
        url:'',
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
        url:'',
        img:'',
        group:'perjadin'
      },
                  {
        name:'Surat Tugas',
        url:'',
        img:'',
        group:'perjadin'
      },
                  {
        name:'Surat Masuk',
        url:'',
        img:'',
        group:'surat'
      },
                        {
        name:'Surat Keluar',
        url:'',
        img:'',
        group:'surat'
      },
                        {
        name:'Dokumen Lelang',
        url:'',
        img:'',
        group:'surat'
      },
                        {
        name:'Lainnya',
        url:'',
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
a {
  color: #42b983;
}
</style>
