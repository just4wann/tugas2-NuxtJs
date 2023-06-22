<script>
  export default {
    props: {
      listArray: Array
    }
  }
</script>

<template>
  <table>
    <tr>
      <th colspan="4" class="title">
        <h3>DAFTAR SISWA</h3>
      </th>
    </tr>
    <tr>
      <th>NO</th>
      <th>NISN</th>
      <th>NAMA LENGKAP</th>
      <th>NILAI</th>
    </tr>
    <tr v-for="(data, index) of listArray">
      <td class="bottom-left">{{ index + 1 }}</td>
      <td>{{ data.nisn }}</td>
      <td>{{ data.nama }}</td>
      <td class="bottom-right">{{ data.nilai }}</td>
    </tr>
  </table>
</template>