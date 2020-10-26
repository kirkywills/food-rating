<template>

  <q-page class="q-pa-lg">
  	<div class="row q-gutter-lg">

			<food
				v-for="food in foods"
				:key="food.id"
				:food="food" />

	    <button-add
	    	@click="showAddFoodModal = true" />

	    <q-dialog
	    	v-model="showAddFoodModal">
        <modal-add-edit-food
        	@close="showAddFoodModal = false"
        	type="add" />
      </q-dialog>

  	</div>
  </q-page>
</template>

<script>
	import { mapGetters } from 'vuex'

	export default {
	  data() {
	  	return {
	  		showAddFoodModal: false
	  	}
	  },
	  computed: {
	  	...mapGetters('foods', ['foods'])
	  },
	  components: {
	  	'food' : require('components/Food.vue').default,
	  	'button-add' : require('components/ButtonAdd.vue').default,
	  	'modal-add-edit-food' : require('components/ModalAddEditFood.vue').default
	  }
	}
</script>
