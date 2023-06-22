<script>

import FormInput from './components/formInput.vue'
import ListSiswa from './components/listSiswa.vue'
import CountAverage from './components/countAvg.vue'

export default {
  data() {
    return {
      daftarSiswa: [],
      nisnSiswa: '',
      namaSiswa: '',
      nilaiSiswa: '',
      avg: ''
    }
  },
  methods: {
    inputData() {
      if (!this.nisnSiswa || !this.namaSiswa || !this.nilaiSiswa) {
        alert('Harap mengisi kolom input!')
      }
      else {
        this.daftarSiswa.push({
          nisn: this.nisnSiswa,
          nama: this.namaSiswa,
          nilai: this.nilaiSiswa
        })
      }
    },
    clear() {
      this.nisnSiswa = '',
      this.namaSiswa = '',
      this.nilaiSiswa = ''
    },
    countAverage() {
      const value = this.daftarSiswa.map(({ nilai }) => nilai)
                                    .map(a => Number(a))
                                    .reduce((acc, curr) => 
                                      acc + curr
                                    );
      const result = value / this.daftarSiswa.length
      if (Math.round(result) === result) {
        return this.avg = result.toString()
      }
      else {
        return this.avg = result.toFixed(2).toString()
      }
    },
    clearAvg() {
      this.avg = ''
    },
    isListed() {
      if ( this.daftarSiswa.length === 0 ) {
        return false
      } else {
        return true
      }
    }
  },
  components: {
    ListSiswa,
    FormInput,
    CountAverage
  }
}
</script>

<template>
  <main :class="{'min-gap' : daftarSiswa.length === 0}">
    <FormInput @insert="inputData" @clear="clear" v-model:nisn="nisnSiswa" v-model:nama="namaSiswa" v-model:nilai="nilaiSiswa"/>
    <section>
      <ListSiswa :listArray="daftarSiswa" v-if="isListed()"/>
      <CountAverage :average="avg" @count="countAverage" @clear="clearAvg" v-if="isListed()"/>
    </section>
  </main>
</template>
