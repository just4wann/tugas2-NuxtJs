<template>
    <tr>
        <td>{{ data.nik }}</td>
        <td>{{ data.nama }}</td>
        <td>{{ data.nilai }}</td>
      </tr>
</template>

<script>
    export default {
        props: {
            data: Object
        }
    }
</script>