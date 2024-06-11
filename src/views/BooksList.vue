<script setup>
import {onBeforeMount} from 'vue'
import {useBookStore} from '../stores/books.js'
import { storeToRefs } from 'pinia'
import {useRouter} from 'vue-router'

const router = useRouter()

const bookStore = useBookStore()
const {fetchAllBooks} = bookStore
const {books}  = storeToRefs(bookStore)


const handleCreateButton = ()=>{
	router.push({
		name:'booksCreateUpdate',
		params:{
			bookId:'new'
		}
	})
}

const handleEditButton = (bookId)=>{
	router.push({
		name:'booksCreateUpdate',
		params:{
			bookId
		}
	})
}

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
					<button @click="handleCreateButton" class='mt-4 icon solid fas fa-book-medical'>ADD</button>
					
				</header>
				<p>
					<table>
						<tr>
							<th>Title</th>
							<th>Author</th>
							<th>Edit</th>
							<th>Delete</th>
						</tr>
						<tr
							v-for="book in books"
							:key="book._id"
						>
							<td>{{book.title}}</td>
							<td>{{book.author.firstName+' '+book.author.lastName}}</td>
							<td><button @click="handleEditButton(book._id)" class='fas fa-pencil-alt' ></button></td>
							<td><button class='solid far fa-trash-alt'></button></td>
						</tr>
					</table>
				</p>
				
			</article>

		</div>
	</section>
</template>

<style>
</style>
