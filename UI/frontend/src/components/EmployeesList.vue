<template>
  <div>
    <h2>Employee List</h2>
    <ul>
      <li v-for="employee in employees" :key="employee.EmployeeId">
        {{ employee.EmployeeName }} - {{ employee.Department }} - {{ employee.DateOfJoining }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      employees: [],
    };
  },
  created() {
    this.getEmployees();
  },
  methods: {
    getEmployees() {
      axios.get('https://localhost:7172/api/employees') 
        .then(response => {
          this.employees = response.data;
        })
        .catch(error => {
          console.error(error);
        });
    },
  },
};
</script>
