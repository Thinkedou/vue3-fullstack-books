<script setup>
import {onBeforeMount} from 'vue'
import {useBookStore} from '../stores/books.js'
import { storeToRefs } from 'pinia'

const bookStore = useBookStore()
const {fetchAllBooks} = bookStore
const {books}  = storeToRefs(bookStore)


onBeforeMount(async ()=>{
	const tryToFetch = await fetchAllBooks()
	console.log(books.value)
})

</script>


<template>
  <section id="main">
	<div class="container">

		<!-- Content -->
			<article class="box post">
				
				<header>
					<h2>Liste Books</h2>
					<p>Combien</p>
				</header>
				<p>
					<table>
						<tr>
							<th>Name</th>
							<th>Type</th>
							<th>Action</th>
						</tr>
						<tr
							v-for="book in books"
							:key="book._id"
						>
							<td>{{book.title}}</td>
							<td>{{book.author.firstName}}</td>
							<td><a href='create-form.html'><button class='fas fa-pencil-alt' ></button></a></td>
							<td><button class='icon solid far fa-trash-alt'></button></td>
						</tr>
					</table>
				</p>
				
			</article>

		</div>
	</section>
</template>

<style>
</style>
