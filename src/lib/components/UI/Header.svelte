<script lang="ts">
	import CropWatchLogo from '$lib/images/favicon.svg';
	import LanguagePicker from './LanguagePicker.svelte';
	import * as m from '$lib/paraglide/messages.js';
	let isMenuOpen = false;
</script>

<header class="sticky top-0 z-50 bg-[#cfecff] shadow-md">
	<!-- Desktop & Tablet Header -->
	<div class="container mx-auto flex items-center justify-between px-6 py-4">
		<!-- Left: Logo and Site Name -->
		<a href="/" class="flex flex-row items-center gap-2">
			<img src={CropWatchLogo} alt="CropWatch Logo" class="h-10" width="40px" height="40px" />
			<h1 class="text-xl font-bold">
				CropWatch<sup><small>®</small></sup>
			</h1>
		</a>

		<!-- Center: Navigation Menu Items (hidden on mobile) -->
		<nav class="hidden flex-1 justify-center space-x-4 md:flex">
			<!-- <a href="/" class="hover:text-blue-600">{m.header_home()}</a> -->
			<!-- <a href="/about-us" class="hover:text-blue-600">About Us</a> -->
			<!-- <a href="#pricing" class="hover:text-blue-600">Pricing</a> -->
			<!-- <a href="/contact-us" class="hover:text-blue-600">{m.contact_us()}</a> -->
		</nav>

		<!-- Right: App Login Button and LanguagePicker (hidden on mobile) -->
		<div class="hidden items-center gap-4 md:flex">
			<a
				href="https://app.cropwatch.io"
				target="_blank"
				rel="noopener"
				class="rounded bg-green-600 px-4 py-2 text-lg font-light text-white hover:bg-green-700"
			>
				{m.app_login()}
			</a>
			<LanguagePicker />
		</div>

		<!-- Mobile: Hamburger Menu Button (shown on mobile only) -->
		<div class="block md:hidden">
			<button
				onclick={() => (isMenuOpen = !isMenuOpen)}
				aria-label="Toggle menu"
				class="text-gray-700 focus:text-gray-900 focus:outline-none"
			>
				<svg class="h-6 w-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
					{#if !isMenuOpen}
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M4 6h16M4 12h16M4 18h16"
						/>
					{:else}
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M6 18L18 6M6 6l12 12"
						/>
					{/if}
				</svg>
			</button>
		</div>
	</div>

	<!-- Mobile Navigation Menu -->
	{#if isMenuOpen}
		<nav class="bg-white shadow-md md:hidden">
			<div class="space-y-2 px-6 py-4 text-center">
				<a href="#home" class="block hover:text-blue-600">{m.header_home()}</a>
				<!-- <a href="about-us" class="block hover:text-blue-600">About Us</a> -->
				<a href="solutions" class="block hover:text-blue-600">Solutions</a>
				<!-- <a href="#pricing" class="block hover:text-blue-600">Pricing</a> -->
				<a href="contact-us" class="block hover:text-blue-600">{m.contact_us()}</a>
				<a
					href="https://app.cropwatch.io"
					target="_blank"
					rel="noopener"
					class="block rounded bg-green-600 px-4 py-2 text-center text-white hover:bg-blue-700"
				>
					App Login
				</a>
				<!-- Optionally, include the language selector for mobile -->
				<div class="mt-4">
					<LanguagePicker />
				</div>
			</div>
		</nav>
	{/if}
</header>
