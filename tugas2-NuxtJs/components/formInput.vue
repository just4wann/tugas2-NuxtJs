<script>
    export default {
        props: {
            nisn: String,
            nama: String,
            nilai: String
        },
        emits: [
            'insert', 
            'clear',
            'update:nisn',
            'update:nama',
            'update:nilai'
        ]
    }
</script>

<template>
    <form class="data-siswa">
      <h3>Masukkan Nilai Tugas Anda</h3>
      <input type="text" class="nisn" placeholder="NISN" :value="nisn" @input="$emit('update:nisn', $event.target.value)">
      <input type="text" class="nama" placeholder="Nama Lengkap" :value="nama" @input="$emit('update:nama', $event.target.value)">
      <input type="text" class="nilai" placeholder="Nilai Matematika" :value="nilai" @input="$emit('update:nilai', $event.target.value)">
      <button type="button" @click="$emit('insert'), $emit('clear')">Submit</button>
    </form>
</template>