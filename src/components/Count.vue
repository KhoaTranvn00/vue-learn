<template>
	<h1>count work {{ count }}</h1>
	<button @click="onIncrease">increase</button>
	<button @click="onDecrease">Decrease</button>
	<hr />
	<input v-model="msg" />
	<p>{{ msg }}</p>
	<p>Name: {{ name }}</p>
	<p>Name2: {{ getName() }}</p>
	<hr />
	<template v-for="todo in todos">
		<li
			@click="handleClickTodo(todo.todo)"
			:style="{ backgroundColor: todo.isSelect ? 'red' : '#ccc' }"
		>
			{{ todo.todo }}
		</li>
	</template>
	<hr />
	<hr />
</template>

<script>
export default {
	data() {
		return {
			count: 1,
			msg: "khoa",
			name: "",
			todos: [
				{
					todo: "a",
					isSelect: false,
				},
				{
					todo: "b",
					isSelect: true,
				},
				{
					todo: "c",
					isSelect: false,
				},
			],
		};
	},

	watch: {
		// msg(...p) {
		// 	console.log(p);
		// 	console.log("watch run");
		// 	this.name = this.msg;
		// },
	},
	computed: {
		updateName(...p) {
			console.log(p);
			console.log("computed run");
			this.name = this.msg;
		},
	},

	methods: {
		onIncrease() {
			this.count++;
		},
		onDecrease() {
			this.count--;
		},
		getName() {
			console.log("method run");
			return this.msg;
		},
		handleClickTodo(todoName) {
			console.log(todoName);
			this.todos.forEach((todo) => {
				if (todo.todo == todoName) {
					todo.isSelect = !todo.isSelect;
				}
			});
		},
	},
};
</script>
