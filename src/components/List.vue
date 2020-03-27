<template>
  <div class="hello">

    <div id="todo-list-example" class="container-fluid">
      <div class="row">
        <div class="col-md-6 mx-auto">
        <br>
          <h1 class="text-center">Aplikasi Todo List</h1>
          <form v-on:submit.prevent="addNewTask">
            <label for="tasknameinput">Tugas Baru</label>
            <input v-model="taskname" id="tasknameinput" class="form-control" placeholder="Masukkan Tugas Baru">
            <br>
            <button v-if="this.isEdit == false" type="submit" class="btn btn-success btn-block">
              Submit
            </button>
            <button v-else type="button" v-on:click="updateTask()" class="btn btn-primary btn-block  mt-3">
              Update
            </button>
          </form>
          <br><br>
          <p> Daftar </p>
          <table class="table">
            <tr v-for="(todo) in todos" v-bind:key="todo.id" v-bind:title="todo.title">
              <td class="text-left">{{todo.title}}</td>
              <td class="text-right">
                <button v-on:click="editTask(todo.title, todo._id)" class=" btn btn-dark ">Edit</button>
                <button v-on:click="deleteTask(todo._id)" class=" btn btn-danger ">Delete</button>
              </td>
            </tr>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
const baseURL = 'http://localhost:3000/api/tasks/';
// const axios = require('axios');
export default {
  data () {
    return {
      todos: [],
      id: '',
      taskname: '',
      isEdit: false
    }
  },
  mounted () {
    this.getTasks()
  },
  methods: {
    getTasks () {
      axios({ method: 'GET', baseURL }).then(
        result => {
          console.log(result.data)
          this.todos = result.data
        },
        error => {
          console.error(error)
        }
      )
    },
    addNewTask () {
      axios.post(baseURL,
        { title: this.taskname }
      ).then((res) => {
        this.taskname = ''
        this.getTasks()
        console.log(res)
      }).catch((err) => {
        console.log(err)
      })
    },
    editTask (title, id) {
      this.id = id
      this.taskname = title
      this.isEdit = true
    },
    updateTask (id) {
      axios.put(baseURL + id,
        { title: this.taskname }
      ).then((res) => {
        this.taskname = ''
        this.isEdit = false
        this.getTasks()
        console.log(res)
      }).catch((err) => {
        console.log(err)
      })
    },
    deleteTask (id) {
      axios.delete(baseURL + id
      ).then((res) => {
        this.taskname = ''
        this.getTasks()
        console.log(res)
      }).catch((err) => {
        console.log(err)
      })
    }
  }
}
</script>