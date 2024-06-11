<script setup>
import {ref,onBeforeMount,computed} from 'vue'
import {useRoute} from 'vue-router'
import {useBookStore} from '@/stores/books.js'
import { storeToRefs } from 'pinia'

const route = useRoute()
const bookStore = useBookStore()

const onEditMode = ref(false)


const pageTitle = computed(()=>{
	return onEditMode.value?'EDITION':'CREATION'
})
const btnLabel = computed(()=>{
	return onEditMode.value?'update':'create'
})

onBeforeMount(()=>{
	const {params} = route 
	if(params.bookId==='new'){
		onEditMode.value = false
	}else{
		onEditMode.value = true
	}
})


</script>

<template>
  <section id="main">
		<div class="container">
		<!-- Content -->
			<h2 class="mb-2">{{ pageTitle }}</h2>

				<form>
					<div class="row gtr-50 ">
						<div class="col-6 col-12-small">
							<input name="name" placeholder="Name" type="text">
						</div>
						<div class="col-6 col-12-small">
							<input name="email" placeholder="Email" type="text">
						</div>
						<div class="col-12">
							<textarea name="message" placeholder="Message"></textarea>
						</div>
						<div class="col-12">
							<a href="#" class="form-button-submit button icon solid fa-pen">{{btnLabel}}</a>
						</div>
					</div>
				</form>

		</div>
	</section>
</template>

<style>
</style>
