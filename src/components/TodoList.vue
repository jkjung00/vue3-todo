<template>
	<div>
		<TransitionGroup name="list" tag="ul">
			<li v-for="(todoItem, index) in propsData" :key="todoItem.item" class="shadow">
				<span class="checkBtn" :class="{checkBtnCompleted: todoItem.completed}" @click="toggleComplete(todoItem, index)">
					<i class="fa-solid fa-check"></i>
				</span>
				<span :class="{textCompleted: todoItem.completed}">{{ todoItem.item }}</span>
				<span class="removeBtn" @click="removeTodo(todoItem, index)">
					<i class="fa fa-trash-alt"></i>
				</span>
			</li>
		</TransitionGroup>
	</div>
</template>

<script>
export default {
	props: ['propsData'],
	methods: {
		removeTodo(todoItem, index) {
			this.$emit('removeItem', todoItem, index)
		},
		toggleComplete(todoItem, index) {
			this.$emit('toggleItem', todoItem, index)
		}
	},
}
</script>

<style scoped>
ul {
	list-style-type: none;
	padding-left: 0;
	margin-top: 0;
	text-align: left;
}
li {
	display: flex;
	min-height: 50px;
	height: 50px;
	line-height: 50px;
	margin: 0.5rem 0;
	padding: 0 0.9rem;
	background: white;
	border-radius: 5px;
}
.removeBtn {
	margin-left: auto;
	color: #de4343;
	cursor: pointer;
}
.checkBtn {
	line-height: 45px;
	color: #62acde;
	margin-right: 5px;
	cursor: pointer;
}
.checkBtnCompleted {
	color: #b3adad;
}
.textCompleted {
	text-decoration: line-through;
	color: #b3adad;
}
/* list item transition */
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateX(30px);
}

</style>