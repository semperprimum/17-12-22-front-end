<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Ф.И.О.</label>
      <input type="text" v-model="name" name="name" placeholder="Добавьте Ф.И.О."  required/>
    </div>
    <div class="form-control">
      <label>Дата выдачи зарплаты</label>
      <input
        type="date"
        v-model="date"
        name="date"
        required
      />
    </div>
    <div class="form-control">
      <label>Количествово отработанных дней</label>
      <input
        type="text"
        v-model="days"
        name="days"
        placeholder="Добавить кол-во отработанных дней"
        required
      />
    </div>
    <div class="form-control">
      <label>Размер зарплаты</label>
      <input
        type="text"
        v-model="salary"
        name="salary"
        placeholder="Добавить зарплату"
        required
      />
    </div>

    <input type="submit" value="Добавить работника" class="btn btn-block" />
  </form>
</template>

<script>

export default {
    name: 'AddWorker',
    data() {
        return {
        name: '',
        date: '',
        days: '',
        salary: '',
        }
    },
    methods: {
      onSubmit(e) {
        e.preventDefault(e)

        const newWorker = { 
          id: Math.floor(Math.random() * 1000),
          name: this.name,
          date: this.date,
          days: this.days,
          salary: this.salary,
          salaryTax: Number(this.salary) - Number(this.salary) * 0.15
        }

        console.log(newWorker)

        this.$emit('add-worker', newWorker)

        this.name = ''
        this.date = ''
        this.days = ''
        this.salary = ''
      }
    }
}
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 500px;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
  border: 1px solid black;
  border-radius: 5px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}

.btn {
    background: black;
    color: white;
    border: 0;
}
</style>