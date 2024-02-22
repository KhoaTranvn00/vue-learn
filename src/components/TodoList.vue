<template>
	<h3>Todo List</h3>
	<input @keyup.enter="handleEnter" v-model="input" ref="inputElement" />
	<button v-if="!todoUpdate" @click="handleAdd">Add</button>
	<template v-else>
		<button @click="handleUpdateTodo">update</button>
		<button @click="todoUpdate = null">cancel</button>
	</template>
	<p v-if="todos.length === 0">Don't have any item. please add more</p>
	<ul v-else>
		<template v-for="todo in todos">
			<li>
				<button @click="onUpdateClick(todo)">update</button>
				<button @click="handleDelete(todo.id)">delete</button>
				<button>hightLight</button>
				<span @click="handleClickTodo(todo)">{{ todo.todo }}</span>
			</li>
		</template>
	</ul>
</template>

<script>
function generateRandomId() {
	return Math.random().toString(36).substr(2, 9);
}

export default {
	data() {
		return {
			todos: [
				{
					id: generateRandomId(),
					todo: "a",
					isHighlight: false,
				},
				{
					id: generateRandomId(),
					todo: "b",
					isHighlight: true,
				},
			],
			input: "",
			todoUpdate: null,
		};
	},

	computed: {
		getStyleTodoItem(todo) {
			return {
				backgroundColor: todo.isHighlight ? "red" : "#ccc",
				// textDecoration: todo.id === todoUpdate?.id ? "underline" : "none",
			};
		},
	},

	methods: {
		handleAdd() {
			this.todos.push({
				id: generateRandomId(),
				todo: this.input,
				isHighlight: false,
			});
			console.log(this.todos);
			this.input = "";
		},
		handleClickTodo(itemClick) {
			this.todos.forEach((todo) => {
				if (todo.id === itemClick.id) {
					todo.isHighlight = !todo.isHighlight;
				}
			});
		},
		onUpdateClick(todo) {
			this.input = todo.todo;
			this.todoUpdate = todo;
			this.$refs.inputElement.focus();
		},
		handleUpdateTodo() {
			this.todos.forEach((todo) => {
				if (todo.id === this.todoUpdate?.id) {
					todo.todo = this.input;
					this.input = "";
					this.todoUpdate = null;
					return;
				}
			});
		},
		handleEnter() {
			if (!this.todoUpdate) {
				this.handleAdd();
			} else this.handleUpdateTodo();
		},
		handleDelete(id) {
			this.todos = this.todos.filter((todo) => todo.id !== id);
		},
	},
};
</script>

<style>
span {
	display: inline-block;
	text-align: center;
	width: 30px;
	height: 30px;
}
</style>
