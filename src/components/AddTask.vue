<template>
	<form @submit="onSubmit" class="add-form">
		<div class="form-control">
			<label>Task</label>
			<input
				type="text"
				v-model="text"
				name="text"
				placeholder="Add Task"
				required
			/>
		</div>
		<div class="form-control">
			<label>Date</label>
			<input
				type="text"
				v-model="date"
				name="date"
				placeholder="Add Date"
				required
			/>
		</div>
		<div class="form-control form-control-check">
			<label>Set Reminder</label>
			<input type="checkbox" v-model="reminder" name="reminder" />
		</div>

		<input type="submit" value="Save Task" class="btn btn-block" />
	</form>
</template>

<script>
export default {
	name: 'AddTask',
	data() {
		// binding this data to input-elements using v-model
		return {
			text: '',
			date: '',
			reminder: false,
		}
	},
	methods: {
		onSubmit(e) {
			e.preventDefault()

			// creating new task object on form submit
			const newTask = {
				id: Math.floor(Math.random() * 100000),
				text: this.text,
				date: this.date,
				reminder: this.reminder,
			}

			this.$emit('add-task', newTask)

			// setting form to initial-state
			this.text = ''
			this.date = ''
			this.reminder = false
		},
	},
	emits: ['add-task'],
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
	width: 100%;
	height: 40px;
	margin: 5px;
	padding: 3px 7px;
	font-size: 17px;
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
</style>
