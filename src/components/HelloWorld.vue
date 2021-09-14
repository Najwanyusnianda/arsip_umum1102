<template>
  <div class="bg-gray-100 dark:bg-gray-800 rounded-2xl h-screen overflow-hidden relative">
    <header class="w-full shadow-lg bg-white dark:bg-gray-700 items-center h-16 rounded-2xl z-40">
      <div class="relative z-20 flex flex-col justify-center h-full px-3 mx-auto flex-center">
        <div class="relative items-center pl-1 flex w-full lg:max-w-68 sm:pr-2 sm:ml-0">
          <div class="overflow-hidden container relative left-0 z-50 flex h-auto h-full hidden md:block sm:visible sm:w-2/12 ">
            <div class="relative flex items-center">
              <span class="text-xl font-mono font-bold mt-2"> Arsip Digital 1102</span>
            </div>
          </div>
          <div class=" overflow-auto container relative left-0 z-50 flex w-7/12 sm:w-7/12 h-auto h-full mr-3 ">
            <div class="ml-3 relative flex items-center w-full lg:w-5/6 h-full group">
              <div
                class="absolute z-50 flex items-center justify-center block w-auto h-10 p-3 pr-2 text-sm text-gray-500 uppercase cursor-pointer sm:hidden">
                <svg fill="none" class="relative w-5 h-5" stroke-linecap="round" stroke-linejoin="round"
                  stroke-width="2" stroke="currentColor" viewBox="0 0 24 24">
                  <path d="M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z">
                  </path>
                </svg>
              </div>
              <svg
                class="absolute left-0 z-20 hidden w-4 h-4 ml-4 text-gray-500 pointer-events-none fill-current group-hover:text-gray-400 sm:block"
                xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path
                  d="M12.9 14.32a8 8 0 1 1 1.41-1.41l5.35 5.33-1.42 1.42-5.33-5.34zM8 14A6 6 0 1 0 8 2a6 6 0 0 0 0 12z">
                </path>
              </svg>
              <input type="text" v-model="search"
                class="block w-full py-1.5 pl-10 pr-4 leading-normal rounded-2xl focus:border-transparent focus:outline-none focus:ring-2 focus:ring-blue-500 ring-opacity-90 bg-gray-100 dark:bg-gray-800 text-gray-400 aa-input"
                placeholder="Search" />

            </div>
          </div>
          <div class="relative p-1 flex items-center justify-end w-3/12 ml-5 mr-4 sm:mr-0 sm:right-auto">
            <div class="relative inline-block text-left">
              <div>
                <button type="button" @click="openKategori"
                  class=" border border-gray-300 bg-white dark:bg-gray-800 shadow-sm flex items-center justify-center w-full rounded-md  px-4 py-2 text-sm font-medium text-gray-700 dark:text-gray-50 hover:bg-gray-50 dark:hover:bg-gray-500 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-gray-100 focus:ring-gray-500"
                  id="options-menu">
                  {{ kategori ? kategori : "Kategori" }}
                  <svg width="20" height="20" fill="currentColor" viewBox="0 0 1792 1792"
                    xmlns="http://www.w3.org/2000/svg">
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
          </div>
        </div>
      </div>
    </header>
    <br>
    <br>
    <div class="overflow-auto h-screen pb-24 pt-2 pr-2 pl-2 md:pt-0 md:pr-0 md:pl-0">
      <div class="grid grid-cols-1 md:grid-cols-3 lg:grid-cols-4 gap-4 my-4">
        <div class="w-full  " v-for="item in filteredFolders" :key="item.name" >
          <div class=" mx-3 -ml-1 shadow-lg px-4 py-6 w-full bg-white rounded-md dark:bg-gray-700 relative cursor-pointer font-mono hover:bg-blue-500 hover:text-white" @click="redirectLink(item.url)" >
            {{item.supername}}
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
    data() {
      return {
        kategori: '',
        active: false,
        search: '',
        filtered_folder: '',
        folders: [{supername:'LPJ',
            name: 'LPJ',
            url: 'https://drive.google.com/drive/folders/1I0-ZNAX-hst9uWaucTexNLC0xRQDy4pr?usp=sharing',
            img: '',
            group: 'bendahara'
          }, {supername:'SP2D',
            name: 'SP2D',
            url: 'https://drive.google.com/drive/folders/1CrwoXLDFmS8HGKcro2dSCBQzeA8ZtHJG?usp=sharing',
            img: '',
            group: 'bendahara'
          }, {supername:'SPJ',
            name: 'pertanggungjawaban, surat, keuangan, kwitansi',
            url: 'https://drive.google.com/drive/folders/1ql_ZhCbs7xrTlcHkLrRmN0wDgRnoOL1w?usp=sharing',
            img: '',
            group: 'bendahara'
          }, {supername:'SPM',
            name: 'SPM',
            url: 'https://drive.google.com/drive/folders/16olhI5JLwIYrtPZi2nPNsHpQqoSUOrFt?usp=sharing',
            img: '',
            group: 'bendahara'
          },
          {supername:'Renstra',
            name: 'reviu, notulensi, daftar, hadir, skp, ckp, pembahasan, 2021, 2020, 2024, monitoring, triwulan',
            url: 'https://drive.google.com/drive/folders/1wRXGWZjRpZEvSuDHCQCkdMPdl0VO4xfX?usp=sharing',
            img: '',
            group: 'sakip'
          }, {supername:'IKU',
            name: 'indikator, kinerja, utama, tahun',
            url: 'https://drive.google.com/drive/folders/14zq6lQdjm3yrBFuU4kIqTMG_70BQnz7i?usp=sharing',
            img: '',
            group: 'sakip'
          },
          {supername:'IKI',
            name: 'indikator, kinerja, individu',
            url: 'https://drive.google.com/drive/folders/1DmVE-25aeLoYF04iHa-vy7ouzFHhYB8b?usp=sharing',
            img: '',
            group: 'sakip'
          }, {supername:'LKIN',
            name: 'LKIN',
            url: 'https://drive.google.com/drive/folders/1wRXGWZjRpZEvSuDHCQCkdMPdl0VO4xfX?usp=sharing',
            img: '',
            group: 'sakip'
          },
          {supername:'FRA',
            name: 'persentase, publikasi, statistik, data, target, singkil',
            url: 'https://drive.google.com/drive/folders/1yMeqiiHC--TkGxVzl-k3zZ-c7dJ82QpE?usp=sharing',
            img: '',
            group: 'sakip'
          },
          {supername:'PK',
            name: 'perjanjian kinerja, surat, nomor, ',
            url: 'https://drive.google.com/drive/folders/1BsoyNGonDE18U1f-WEg7jUcxDuA80viX?usp=sharing',
            img: '',
            group: 'sakip'
          },
          {supername:'Laporan Keuangan',
            name: 'bmn, neraca, aset, GL, keuangan, pengelola',
            url: 'https://drive.google.com/drive/folders/13zxUaJ0E9OZYm0QeKMsrRqA_TH8ld8b_?usp=sharing',
            img: '',
            group: 'keuangan'
          },
          {supername:'Laporan Perjadin',
            name: 'Laporan Perjadin',
            url: '',
            img: '',
            group: 'perjadin'
          },
          {supername:'SPD',
            name: 'surat, perjalanan, dinas',
            url: 'https://drive.google.com/drive/folders/1pypBUl1vJ6EmQqOanQ_jG4Z6zrZkDabq?usp=sharing',
            img: '',
            group: 'perjadin'
          },
          {supername:'Surat Tugas',
            name: 'Surat, tugas, ST, perjalanan, hari, tempat, acara',
            url: 'https://drive.google.com/drive/folders/1GBDVNXOT5a8pLcIp8B5X1B6WXYgVgmAz?usp=sharing',
            img: '',
            group: 'perjadin'
          },
          {supername:'Surat Masuk',
            name: 'surat, masuk, keluar',
            url: 'https://drive.google.com/drive/folders/1Yz6SEN4hvucLqx943KOebdg_ZHqPuTHM?usp=sharing',
            img: '',
            group: 'surat'
          },
          {supername:'Surat Keluar',
            name: 'keluar, perihal, rapat, undangan,',
            url: 'https://drive.google.com/drive/folders/1t2GBZF4KFtTTeK5DOVFM9sk33RvorCyR?usp=sharing',
            img: '',
            group: 'surat'
          },
          {supername:'Dokumen Lelang',
            name: 'bast, sepeda motor, lelang, dokumen, bpkb, stnk, rumah dinas, kib',
            url: 'https://drive.google.com/drive/folders/1mDFpD-hAyvL-MgHnKBQFfxpj0sezIdiZ?usp=sharing',
            img: '',
            group: 'surat'
          },
          {supername:'Lainnya',
            name: 'surat, keterangan,',
            url: 'https://drive.google.com/drive/folders/1esA1XCIycdfXkDs23IiYxBNvR7QLi0rI?usp=sharing',
            img: '',
            group: 'surat'
          },
          {supername:'SOP',
            name: 'SOP',
            url: 'https://drive.google.com/drive/folders/1YQEVQXGwGoi-fAGbjSHPThSv5J92bdaU?usp=sharing',
            img: '',
            group: 'sop'
          },
          {supername:'Data Pegawai',
            name: 'Data Pegawai',
            url: 'https://drive.google.com/drive/folders/1O4pbyjR-FTGEh6g491cPgzTOkYXUS1T0?usp=sharing',
            img: '',
            group: 'kepegawaian'
          },



        ]
      }
    },
    computed: {
      filteredFolders() {
        return this.folders.filter(folder => {

            if (this.search != null && this.kategori != '') {
              return folder.name.indexOf(this.search) > -1 && folder.group == this.kategori
            } else if (this.kategori != '') {
              return folder.group == this.kategori
            } else if (this.search != null) {
              return folder.name.indexOf(this.search) > -1
            }

          }

        )
      }
    },
    methods: {
      filterCategory(kategori) {
        this.active = !this.active
        return this.kategori = kategori
      },
      openKategori() {
        this.active = !this.active
      },
      resetFolders() {
        this.kategori = '',
          this.active = false,
          this.search = null
      },
      redirectLink(url){
         window.open(url, "_blank"); 
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