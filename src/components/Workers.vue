<template>
 <table border="0" style="width:95%" >
    <tr>
        <th style="width: 100px">ID</th>
        <th style="width: 250px">ФИО</th>
        <th style="width: 150px">Дата выдачи зарплаты</th>
        <th style="width: 150px">Отработанные дни</th>
        <th style="width: 230px">Зарплата</th>
        <th>Зарплата c НДС</th>
    </tr>
    </table>
    <div :key="worker.id" v-for="worker in workers">
            <Worker @delete-worker="$emit('delete-worker', worker.id)" :worker="worker" />
    </div>
</template>

<script>
import Worker from './Worker.vue'

export default {
    name: 'Worksers',
    props: {
        workers: Array
    },
    components: {
        Worker,
    },
    emits: ['delete-worker'],
}
</script>

<style scoped>
</style>