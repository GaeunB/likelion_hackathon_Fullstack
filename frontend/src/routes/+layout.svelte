<script lang="ts">
	import '../app.postcss';
	import {
		Avatar,
		DarkMode,
		Dropdown,
		DropdownDivider,
		DropdownHeader,
		DropdownItem,
		Label,
		Sidebar,
		SidebarGroup,
		SidebarItem,
		SidebarWrapper
	} from 'flowbite-svelte';

	let width: number;
</script>

<svelte:window bind:innerWidth={width} />

<div class="flex min-h-screen bg-white">
	<div class="flex flex-col mx-full w-full">
		<!-- <div class="my-4 w-full flex justify-end">
			<div class="flex items-center space-x-4">
				<Avatar id="user-drop" size="xs" />

				<Dropdown triggeredBy="#user-drop">
					<DropdownHeader>
						<span class="block text-sm">User</span>
					</DropdownHeader>
					<DropdownItem href="/settings">Settings</DropdownItem>
					<DropdownDivider />
					<DropdownItem href="/logout">Sign out</DropdownItem>
				</Dropdown>
			</div>

			<DarkMode class="mx-2" />
		</div> -->
		<main class="w-full h-full mx-full">
			<slot />
		</main>
	</div>
</div>
