<template>
<div class="container">
  <Header title="Учет заработной платы" />
  <AddWorker @add-worker="addWorker"/>
  <Workers @delete-worker="deleteWorker" :workers="workers" />
  <footer>
    <p> Сумма ЗП без учета НДС: {{totalSalary}}</p>
    <p>Сумма ЗП с учетом НДС: {{totalSalaryTax}}</p>
  </footer>
</div>
</template>

<script>
import Header from './components/Header'
import Workers from './components/Workers'
import AddWorker from './components/AddWorker'


export default {
  name: "App",
  components: {
    Header,
    Workers,
    AddWorker,
  },
  data() {
    return {
      workers: [],
      totalSalary: 0,
      totalSalaryTax: 0
    }
  },
  methods: {
    addWorker(worker) {
      this.workers = [...this.workers, worker]
      this.totalSalary = this.updateSalary()
      this.totalSalaryTax = this.updateSalaryTax()
    },

    deleteWorker(id) {
      if(confirm('Вы уверены?'))  {
        this.workers = this.workers.filter((worker) => worker.id !== id)
      }
    },
    updateSalary() {
      let total = 0;
      for (const worker of this.workers) {
        total += Number(worker.salary);
      }
      return total.toFixed(2);
    },
    updateSalaryTax() {
      let total = 0;
      for(const worker of this.workers) {
        total += Number(worker.salaryTax);
      }
      return total.toFixed(2);
    }
  },
  created() {
    this.workers = [
      {
        id: 1,
        name: 'John Doe',
        date: '2022-12-01',
        days: '22',
        salary: 250000,
        salaryTax: 212500,
      },
      {
        id: 2,
        name: 'Marie Doe',
        date: '2022-12-02',
        days: '23',
        salary: 280000,
        salaryTax: 238000,
      },
      {
        id: 3,
        name: 'John Smith',
        date: '2022-12-03',
        days: '21',
        salary: 200000,
        salaryTax: 170000,
      },
    ]
    this.totalSalary = this.updateSalary()
    this.totalSalaryTax = this.updateSalaryTax()
  },
}
</script> 

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 1300px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}


.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 300px;
}
</style>
