<template>
  <div id="app">
    <header class="header">
      <h1>Student Profiles</h1>

      <!-- Form for adding new student -->
      <form @submit.prevent="addStudent" className="add-student-form">
        <input v-model="newStudentName" placeholder="Enter Name" />
        <input v-model="newStudentCountry" placeholder="Enter Country" />
        <button type="submit">Add Student</button>
      </form>
    </header>




    <!-- Display a message if no students -->
    <p v-if="students.length === 0">No students available</p>

    <!-- List of students using v-for -->
    <ul>
      <li v-for="student in students" :key="student.phoneNumber">
        <div class="student-profile">
          <img :src="student.profilePicture" alt="Profile Picture" />
          <h3 v-text="student.fullName"></h3>
          <p v-text="student.description"></p>
          <p><strong>Country:</strong> {{ student.country }}</p>
          <p><strong>Address:</strong> {{ student.address }}</p>

          <!-- Conditional rendering based on student country -->
          <p v-if="student.country === 'United States'">Located in the USA</p>
          <p v-else-if="student.country === 'Canada'">Located in Canada</p>
          <p v-else-if="student.country === 'Nigeria'">Located in Nigeria</p>
          <p v-else>From another country</p>

          <!-- Button to delete student -->
          <button v-on:click="removeStudent(student.phoneNumber)">Delete</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      students: [
        {
          "fullName": "Alice Johnson",
          "description": "A skilled front-end developer specializing in Vue.js and React. Alice has a knack for designing beautiful and responsive web applications that meet user needs.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8902",
          "country": "Canada",
          "address": "456 Maple Ave, Toronto, ON"
        },
        {
          "fullName": "Michael Smith",
          "description": "An enthusiastic software engineer with a focus on Vue.js and back-end integration. Michael loves tackling complex problems and delivering efficient solutions.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8903",
          "country": "Australia",
          "address": "789 Pine St, Sydney, NSW"
        },
        {
          "fullName": "Jessica Brown",
          "description": "A creative web developer with a strong background in Vue.js and user experience design. Jessica is dedicated to crafting intuitive interfaces that engage users.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8904",
          "country": "United Kingdom",
          "address": "101 High St, London"
        },
        {
          "fullName": "David Wilson",
          "description": "A motivated full-stack developer with experience in Vue.js and Node.js. David enjoys building robust applications that are both functional and visually appealing.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8905",
          "country": "Germany",
          "address": "202 Elm St, Berlin"
        },
        {
          "fullName": "Emily Davis",
          "description": "A detail-oriented software developer with expertise in Vue.js and agile methodologies. Emily is passionate about delivering high-quality code and improving development processes.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8906",
          "country": "France",
          "address": "303 Oak St, Paris"
        },
        {
          "fullName": "Chris Martin",
          "description": "An innovative web developer specializing in Vue.js and responsive design. Chris enjoys creating seamless user experiences and is always eager to learn new technologies.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8907",
          "country": "Italy",
          "address": "404 Birch St, Rome"
        },
        {
          "fullName": "Sophia Lee",
          "description": "A dynamic software engineer with a focus on Vue.js and cloud technologies. Sophia is passionate about building scalable applications that enhance productivity.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8908",
          "country": "Spain",
          "address": "505 Cedar St, Madrid"
        },
        {
          "fullName": "James Taylor",
          "description": "A resourceful developer with experience in Vue.js and mobile app development. James loves creating applications that bridge the gap between users and technology.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8909",
          "country": "Netherlands",
          "address": "606 Walnut St, Amsterdam"
        },
        {
          "fullName": "Olivia White",
          "description": "A passionate front-end developer with expertise in Vue.js and design systems. Olivia focuses on building accessible and user-friendly interfaces.",
          "profilePicture": "https://placehold.co/600x400",
          "phoneNumber": "+1-234-567-8910",
          "country": "Sweden",
          "address": "707 Cherry St, Stockholm"
        }
      ],
      newStudentName: '',
      newStudentCountry: ''
    };
  },
  methods: {
    // Add new student
    addStudent() {
      if (this.newStudentName && this.newStudentCountry) {
        const newStudent = {
          fullName: this.newStudentName,
          description: "A new Vue.js enthusiast.",
          profilePicture: "https://placehold.co/600x400",
          phoneNumber: `+1-234-567-${Math.floor(Math.random() * 10000)}`,
          country: this.newStudentCountry,
          address: `${this.newStudentName}'s address`
        };
        this.students.push(newStudent);
        this.newStudentName = '';
        this.newStudentCountry = '';
      }
    },
    // Remove a student
    removeStudent(phoneNumber) {
      this.students = this.students.filter(student => student.phoneNumber !== phoneNumber);
    }
  }
};
</script>

<style scoped>
#app {
  font-family: Arial, sans-serif;
  /* padding: 20px; */
  background-image: linear-gradient(to right top, #051937, #004d7a, #008793, #00bf72, #a8eb12);
}

header {
  display: flex;
  padding: 20px;
  justify-content: space-between;
  align-items: center;
  flex-wrap: nowrap;
}

.add-student-form {
  gap: 1rem;
  display: flex;
}

ul {
  list-style-type: none;
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
}

h1 {
  color: #2c3e50;
}

.student-profile {
  background-color: rgb(20, 19, 19);
  color: rgb(223, 213, 213);
  padding: 15px;
  margin: 10px;
  display: flex;
  border-radius: 8px;
  width: 250px;
  flex-wrap: wrap;
  flex-direction: column;
  height: 500px;
  align-content: center;
  align-items: center;
  justify-content: space-between;
}

.student-profile img {
  height: 100px;
  border-radius: 50%;
  margin-right: 10px;
}

button {
  background-color: #e74c3c;
  color: white;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}

button:hover {
  background-color: #c0392b;
}
</style>
