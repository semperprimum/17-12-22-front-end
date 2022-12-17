<template>
<div class="table">
        <table style="width:94.9%">
            <tr>
                <th style="width: 100px">{{worker.id}}</th>
                <td style="width: 250px">{{worker.name}}</td>
                <td style="width: 150px">{{worker.date}}</td>
                <td style="width: 150px">{{worker.days}} дн.</td>
                <td style="width: 230px">{{worker.salary}} тг.</td>
                <td>{{worker.salaryTax}} тг.</td>
            </tr>
        </table> 
    <i @click="onDelete(worker.id)" class="fas fa-times"></i>
</div>
</template>

<script>
export default {
    name: 'Worker',
    props: {
        worker: Object,
    },
    methods: {
        onDelete(id) {
            this.$emit('delete-worker', id)
        }
    }
}

</script>

<style>
.fas {
    color: red;
}

.fas:hover {
    cursor: pointer;
}

table, th, td {
    border: 1px solid black;
    text-align: center;
}

.table {
    display: flex;
    align-items: center;
}

.table table {
    margin-right: 5px;
}
</style>