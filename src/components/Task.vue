<template>
	<div
		@dblclick="$emit('toggle-reminder', task.id)"
		:class="[task.reminder && 'reminder', 'task']"
	>
		<h3>
			{{ task.text }}
			<i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
		</h3>
		<p>{{ task.date }}</p>
	</div>
</template>

<script>
export default {
	name: 'Task',
	props: {
		task: Object,
	},
	emits: ['toggle-reminder', 'delete-task'],
}
</script>

<style scoped>
.fas {
	color: orangered;
}
.task {
	background: #f4f4f4;
	margin: 5px;
	padding: 10px 20px;
	border-left: 5px solid orangered;
	cursor: pointer;
}
.task.reminder {
	border-left: 5px solid green;
}
.task h3 {
	display: flex;
	align-items: center;
	justify-content: space-between;
}
</style>
