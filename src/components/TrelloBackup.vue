<template>
  <div class="main-area">
    <h2 class="text-center p-2 mb-0 mt-3">Trello Board</h2>
    <hr>
    
    <div class="row">
		<div class="col-3">
			<h3>Draggable 1</h3>
			<draggable
				class="list-group"
				:list="list1"
				group="people"
				itemKey="name"
			>
				<template #item="{ element, index }">
					<div class="list-group-item">
						{{ element.name }} {{ index }}
						<p>{{ element.description }}</p>
					</div>
				</template>
			</draggable>
		</div>

		<div class="col-3">
			<h3>Draggable 2</h3>
			<draggable
				class="list-group"
				:list="list2"
				group="people"
				itemKey="name"
			>
				<template #item="{ element, index }">
					<div class="list-group-item">
						{{ element.name }} {{ index }}
						<p>{{ element.description }}</p>
					</div>
				</template>
			</draggable>
		</div>
  </div>

<div class="row mt-4">
	<div class="col-sm-6">
		{{ list1 }}
	</div>
	<div class="col-sm-6">
		{{ list2 }}
	</div>
	<div class="col-sm-12 mt-5">
		{{ mainlist }}
	</div>
</div>

  </div>
</template>

<script>
	import draggable from "vuedraggable";

	export default {
		name: "trello",
		components: {
			draggable
		},
		computed: {
			mainlist() {
				return [...this.list1, ...this.list2];
			}
		},
		data() {
			return {
				list1: [
					{ name: "John", description:"description 1",  id: 1 },
					{ name: "Joao", description:"description 2",  id: 2 },
					{ name: "Jean", description:"description 3",  id: 3 },
					{ name: "Gerard", description:"description 4",  id: 4 }
				],
				list2: [
					{ name: "Juan", description:"description 5",  id: 5 },
					{ name: "Edgard", description:"description 6",  id: 6 },
					{ name: "Johnson", description:"description 7",  id: 7 }
				]
			};
		}
	};
</script>