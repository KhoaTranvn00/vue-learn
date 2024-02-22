<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
import Count from "./components/Count.vue";
import TodoItem from "./components/TodoItem.vue";
import Assignment6 from "./components/Assignment6.vue";
import TodoList from "./components/TodoList.vue";
</script>

<template>
	<header>
		<div class="wrapper">
			<TodoList></TodoList>
			<hr />
			<Assignment6></Assignment6>
			<hr />
			<Count></Count>
			<HelloWorld msg="You did it!" />

			<TodoItem msg="asd123"></TodoItem>
		</div>
	</header>
</template>
