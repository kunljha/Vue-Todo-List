<template>
	<div class="container">
		<Header
			@btn-click="toggleAddTask"
			title="Task List"
			:showAddTask="showAddTask"
		/>
		<div v-show="showAddTask">
			<AddTask @add-task="addTask" :showAddTask="showAddTask" />
		</div>
		<Tasks
			@delete-task="deleteTask"
			@toggle-reminder="toggleReminder"
			:tasks="tasks"
		/>
	</div>
</template>

<script>
import Header from './components/Header.vue'
import Button from './components/Button.vue'
import AddTask from './components/AddTask.vue'
import Tasks from './components/Tasks.vue'

export default {
	name: 'App',
	components: {
		Header,
		Button,
		AddTask,
		Tasks,
	},
	data() {
		return {
			tasks: [],
			showAddTask: false,
		}
	},
	methods: {
		// toggle AddTask component
		toggleAddTask() {
			this.showAddTask = !this.showAddTask
		},

		// add a new task
		addTask(task) {
			this.tasks = [...this.tasks, task]
		},

		// delete a task
		deleteTask(id) {
			this.tasks = this.tasks.filter((task) => task.id !== id)
		},

		// toggle reminder of a task
		toggleReminder(id) {
			this.tasks = this.tasks.map((task) =>
				task.id === id ? { ...task, reminder: !task.reminder } : task
			)
		},
	},
	created() {
		this.tasks = [
			{
				id: 1,
				text: 'Task One',
				date: 'Feb 12, 2022',
				reminder: true,
			},
			{
				id: 4,
				text: 'Task Two',
				date: 'Feb 11, 2022',
				reminder: false,
			},
			{
				id: 3,
				text: 'Task Three',
				date: 'Feb 13, 2022',
				reminder: true,
			},
		]
	},
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
	box-sizing: border-box;
	margin: 0;
	padding: 0;
}
body {
	font-family: 'Poppins', sans-serif;
}
.container {
	max-width: 500px;
	min-height: 300px;
	margin: 30px auto;
	overflow: auto;
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
	width: 100%;
}
</style>
