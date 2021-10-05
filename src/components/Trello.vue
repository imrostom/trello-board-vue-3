<template>
	<!-- Masthead -->
	<header class="masthead p-4">
		<div class="logo">
			<h1><i class="fab fa-trello logo-icon" aria-hidden="true"></i>Trello</h1>
		</div>
	</header>
	<!-- End of masthead -->
	<!-- Lists container -->
	<section class="lists-container pt-3">
		<div class="list" v-for="(list, index) in lists" :key="index">
			<h3 class="list-title">{{ list.label }}</h3>
			<draggable
				class="list-items"
				:list="list.items"
				group="people"
				itemKey="name"
				:component-data="{ tag: 'ul' }"
				ghost-class="ghost"
				chosen-class="chosen"
				drag-class="drag"
				@end="updateItemOrder"
			>
				<template #item="{ element, index }">
					<li>
						{{ element.name }} {{ index }}
						<p>{{ element.description }}</p>
					</li>
				</template>
			</draggable>
		</div>

		{{ lists }}

	</section>
</template>

<script>
	import draggable from "vuedraggable";

	export default {
		name: "trello",
		components: {
			draggable
		},
		methods: {
			updateItemOrder() {
				console.log(this.lists);
			}
		},
		data() {
			return {
				lists:[
					{
						'label': 'Todo',
						'items':[
							{ name: "John", description:"description 1",  id: 1 },
							{ name: "Joao", description:"description 2",  id: 2 },
							{ name: "Jean", description:"description 3",  id: 3 },
							{ name: "Gerard", description:"description 4",  id: 4 }
						]
					},
					{
						'label': 'Bug',
						'items': [
							{ name: "Juan", description:"description 5",  id: 5 },
							{ name: "Edgard", description:"description 6",  id: 6 },
							{ name: "Johnson", description:"description 7",  id: 7 }
						]
					},
					{
						'label': 'Complete',
						'items': [
							{ name: "Juan", description:"description 8",  id: 8 },
							{ name: "Edgard", description:"description 9",  id: 9 },
						]
					}
				]
			};
		}
	};
</script>


<style>
	.chosen {
		opacity: 0.5;
		background: blue;
	}
	
	.chosen.ghost {
		opacity: 0;
		background: red;
	}

	.drag {
		opacity: 0.5;
		background: green;
	}
</style>