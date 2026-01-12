<template>
  <div>
<h3> Students grades </h3>


<div class="container">
    <table class="StudentGrades">
          <tr>
            <th>St. Code</th>
            <th>Homework 1</th>
            <th>Homework 2</th>
            <th>Exam</th>
            <th>Final grade</th>
          </tr>
          <tr class="item" v-for="grade in grades" :key="grade.id">
            <td><p>{{ grade.studentcode }}</p></td>
            <td><p>{{ grade.hw1 }}</p></td>
            <td><p>{{ grade.hw2 }}</p></td>
            <td><p>{{ grade.exam }}</p></td>
            <td><p>{{ grade.final }}</p></td>
            
          </tr>
      </table>
</div>
</div>
</template>

<script>
export default {
  name: "Students",
  data() {
    return {
      grades: [],
    };
  },
  methods: {
    fetchRecords() {
      fetch(`http://localhost:3000/api/grades`)
        .then((response) => response.json())
        .then((data) => (this.grades = data))
        .catch((err) => console.log(err.message));
  },
  },
  

  mounted() {
    const gradeData = this.fetchRecords();
    console.log("mounted");
    console.info(gradeData)
  } 
};
</script>

<style scoped>
h1 {
  font-size: 20px;
}

.StudentGrades {
  display: block;
  margin: 0 auto;
  padding: 10px 20px;
  margin-bottom: 1em;
  margin-left: 5rem ;
  margin-right: 5rem;
  background: rgb(184, 184, 184);
  border-radius: 1px;


  color: rgb(32, 34, 50);
  text-decoration: none;
  text-align: center;
  align-items: center;
  
}

.StudentGrades th {
  padding-left: 20px;
}

</style>
