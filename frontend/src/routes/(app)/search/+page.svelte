<script lang="ts">
	import { enhance } from '$app/forms';
	import { Card, Label, Input, Button, Fileupload } from 'flowbite-svelte';

	let value: any;
	export let urls: any[] = [];
	let loading = false;

	async function handleSubmit(event: Event) {
		const form = event.target as HTMLFormElement;
		const formData = new FormData(form);
		loading = true;

		const response = await fetch(form.action, {
			method: "POST",
			body: formData,
		});

		const result = await response.json(); 

		if (result.data) {
			urls = JSON.parse(result.data).slice(2, 7);
		} else {
			console.error("Unexpected data format received:", result);
		}

		loading = false;
	}
</script>

<div class="flex justify-center items-center min-h-screen mx-auto">
	<div class="m-20 w-full max-w-4xl">
		<h1 class="mb-4 text-2xl font-extrabold text-gray-900 dark:text-white md:text-5xl lg:text-6xl">
			<span class="text-transparent bg-clip-text bg-gradient-to-r to-pink-600 from-pink-400 ">
				검색하기
			</span>
			<p class="mb-10 text-xl text-gray-700 ">
				구매하고자 하는 종류를 검색하세요!
			</p>
			</h1>
		

		
<form >   
	<label for="default-search" class="mb-2 text-sm bg-pink-400 font-medium text-gray-900 sr-only dark:text-white">검색</label>
	<div class="relative">
			<div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
					<svg class="w-4 h-4 text-gray-500 dark:text-gray-400" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 20 20">
							<path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z"/>
					</svg>
			</div>
			<input type="search" id="default-search" class="block w-full p-4 pl-10 text-sm text-gray-900 border border-gray-300 rounded-lg bg-gray-50 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" placeholder="여름용 바지" required>
			<button type="submit" class="bg-pink-400 text-white absolute right-2.5 bottom-2.5 bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-4 py-2 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">검색</button>
	</div>
	
</form>

		<!-- List 5 image URLs -->
		<div class="relative mt-8">
			
			<div class="flex space-x-4 mt-4">
				{#each urls as url (url)}
					<div class="w-1/5 mt-4 flex flex-col">
						<img src={url} alt="" class="object-cover rounded shadow-lg h-32 w-32 mx-auto"/> <!-- h-32와 w-32로 높이와 너비를 지정 -->
					</div>
				{/each}
			</div>
		</div>	
			
	</div>
	</div>
	<footer class="bg-white rounded-lg shadow m-4 dark:bg-gray-800">
		<div class="w-full mx-auto max-w-screen-xl p-4 md:flex md:items-center md:justify-between">
			<span class="text-sm text-gray-500 sm:text-center dark:text-gray-400">© 2023 <a href="#" class="hover:underline">청바지</a>. All Rights Reserved.
		</span>
		<ul class="flex flex-wrap items-center mt-3 text-sm font-medium text-gray-500 dark:text-gray-400 sm:mt-0">
				<li>
						<a href="#" class="mr-4 hover:underline md:mr-6 ">About</a>
				</li>
				<li>
						<a href="#" class="mr-4 hover:underline md:mr-6">Privacy Policy</a>
				</li>
				<li>
						<a href="#" class="mr-4 hover:underline md:mr-6">Licensing</a>
				</li>
				<li>
						<a href="#" class="hover:underline">Contact</a>
				</li>
		</ul>
		</div>
	</footer>
