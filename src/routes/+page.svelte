<script lang="ts">
	import PLANT_IMAGE from '$lib/images/plant.avif';
	import COLD_STORAGE_IMAGE from '$lib/images/refer.jpg';
	import HOT_IMAGE from '$lib/images/hot.png';
	import SectionCard from '$lib/components/UI/Section-Card.svelte';
	// Removed FACTORY_IMAGE import as it's for Safety & Risk mitigation
	// Removed BOSTON_IMAGE import as it's for smart city
	import SAITO_IMAGE from '$lib/images/saito.jpg';
	// import LineCarasol from '$lib/components/UI/Line-Carasol.svelte';
	import * as m from '$lib/paraglide/messages.js';
	import PriceCard from '$lib/components/UI/Price-Card.svelte';
	import { languageTag } from '$lib/paraglide/runtime';
	import { fly } from 'svelte/transition';
	import { ChartColumnIncreasing, Sprout, CircleDollarSign, Shield, RadioTower, Route } from '@lucide/svelte';
	import Modal from '$lib/components/UI/Modal.svelte';
	// let submittingEmail = $state(false);
	let showModalAffordable = $state(false);
	let showModalService = $state(false);
	let showModalHardware = $state(false);
	let showModalCoverage = $state(false);

	let loaded = $state(true); // Set to true since we no longer need to wait for canvas initialization
</script>

<svelte:head>
	<!-- Primary Meta Tags -->
	<title>クロップウォッチ - IoT Monitoring</title>
	<meta name="title" content="クロップウォッチ" />
	<meta
		name="description"
		content="CropWatch the best IoT device for remote monitoring for your farm 🌱, building 🏢."
	/>
	<meta
		name="keywords"
		content="IoT Monitoring, クロップウォッチ, Cold Chain Management, Full service IoT"
	/>
	<meta name="author" content="CropWatch LLC" />

	<meta
		name="description"
		content="CropWatch - Solving problems using IoT for Farming, Industry, and more"
	/>
	<meta name="keywords" content="CropWatch, IoT, Farming, Industry" />
	<meta name="robots" content="index, follow" />
	<link rel="preload" as="image" href={SAITO_IMAGE} />
	<link rel="preload" as="image" href={PLANT_IMAGE} />
	<link rel="preload" as="image" href={COLD_STORAGE_IMAGE} />
	<link rel="preload" as="image" href={HOT_IMAGE} />
</svelte:head>

<!-- Hero Section -->
<section
	id="home"
	class="relative bg-blue-200 py-32 text-white bg-[url(/images/sensor-field2.jpg)] bg-cover bg-fixed min-h-screen"
	style="background-image: url('{SAITO_IMAGE}'); background-position: center;"

>
	<!-- Overlay for blur and darkening -->
	<div class="backdrop-blur-xs absolute inset-0 bg-black bg-opacity-10"></div>
	<!-- Content -->
	<div class="container relative mx-auto text-center px-10 space-y-10">
		{#if loaded}
			<h1 class="text-5xl font-bold text-white xl:text-6xl"
					transition:fly={{ y: 100, duration: 1000 }}>{m.home_hero_title()}</h1>
			<p class="w-full bg-blue-300 rounded-lg mt-10 text-xl lg:mx-auto text-white-900 font-bold bg-opacity-70 p-4"
				 transition:fly={{ y: 100, duration: 1000 , delay: 200 }}>
				{m.home_hero_subtitle()}
			</p>
			<div class="mt-6 lg:w-1/2 lg:mx-auto pt-10" transition:fly={{ y: 100, duration: 1000 , delay: 500 }}>
				<a href="/use-cases"
					 class="bg-green-600 px-4 py-3 text-white text-lg rounded-md hover:bg-gray-200 flex justify-center">
					{m.home_hero_button_label()}
					<ChartColumnIncreasing size={30} class="ml-2 " />
				</a>
			</div>
			<div class="mt-10">
				<!-- If you add any hero image element here, consider adding explicit width/height and loading="lazy" if offscreen -->
			</div>
		{/if}
	</div>
</section>


<!-- Solutions Section -->
<section id="solutions" class="relative bg-gray-100 py-20 bg-gradient-to-t from-white to-blue-300"
				 style="overflow: hidden;">
	<div class="container relative z-10 mx-auto text-center ">
		<h2 class="text-3xl font-bold">{m.home_solutions_title()}</h2>
		<p class="mt-4">{m.home_solutions_subtitle()}</p>
		<div class="mt-10 grid grid-cols-1 gap-8 md:grid-cols-3">
			<SectionCard
				image="/images/sensor-field.jpg"
				title={m.home_solutions_farming_title()}
				description={m.home_solutions_farming_description()}
				link="/product/cw-ss"
				class="bg-green-600"

			/>

			<SectionCard
				image={COLD_STORAGE_IMAGE}
				title={m.home_solutions_cold_storage_title()}
				description={m.home_solutions_cold_storage_description()}
				link="/product/cw-air-th"
				class="bg-blue-500"
			/>

			<SectionCard
				image={HOT_IMAGE}
				title={m.home_solutions_heat_safety_title()}
				description={m.home_solutions_heat_safety_description()}
				link="/product/cw-air-th-safety"
				class="bg-orange-500"
			/>
		</div>
	</div>
</section>
<!--Underground Pause-->
<section id="underground-img">
	<div
		class="h-60 w-full bg-[url(/images/sensor-underground.png)] bg-contain relative lg:bg-cover lg:bg-fixed lg:bg-bottom lg:h-[30rem]">
		<p
			class="font-semibold text-3xl px-4 text-green-500 absolute bottom-6 right-5 mix-blend-lighten flex items-center lg:text-6xl lg:bottom-20">
			Know your crops
			<Sprout color="white" size="30" class="animate-bounce" />
		</p>
	</div>
</section>
<section class="py-20 bg-[#cfecff]">
	<h2 class="text-6xl font-semibold p-10">Why <span class="text-green-500">Us</span>?</h2>
	<div class="flex flex-col lg:flex-row items-center justify-between lg:px-12 px-4 space-y-10 lg:space-y-0">
		<button onclick={() =>(showModalAffordable = true)}
						class="bg-emerald-900 text-white lg:w-1/3 lg:h-[45rem] lg:rounded-l-xl lg:rounded-none rounded-md text-center items-center flex flex-col justify-center space-y-12 lg:space-y-20 py-20 px-8 hover:-translate-y-10 transition ease-in-out">
			<p class="text-4xl font-semibold">Affordable Pricing</p>
			<CircleDollarSign size={150} />
			<p>Enjoy cost-effective solutions with transparent pricing, designed to deliver exceptional value compared to
				industry standards.</p>
		</button>
		<Modal bind:showModal={showModalAffordable}>
			{#snippet header()}
				Affordable Pricing
			{/snippet}
			{#snippet children()}
				<CircleDollarSign size={100} />
				<p>Our pricing model is designed with farmers in mind, offering flexible plans that scale with your needs.
					Whether you're managing a small family farm or a large agricultural enterprise, our IoT crop monitoring
					solutions provide exceptional value without hidden costs. We offer straightforward subscription tiers,
					one-time purchase options for hardware, and no long-term contracts, ensuring you only pay for what you need.
					Compared to industry standards, our solutions deliver premium features at a fraction of the cost, empowering
					you to maximize yields while minimizing expenses.</p>
				<img src="https://images.unsplash.com/photo-1628282928695-29aaa1536c11?q=80&w=2340&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" alt="Stack of coins representing affordable pricing" class="mt-4 w-full h-auto rounded-xl" />
			{/snippet}
		</Modal>
		<button onclick={() =>(showModalService = true)}
						class="bg-green-500 text-white lg:w-1/3 lg:h-[45rem] text-center items-center rounded-md lg:rounded-none flex flex-col justify-center space-y-12 lg:space-y-20 py-20 px-8 hover:-translate-y-10 transition ease-in-out">
			<p class="text-4xl font-semibold">End-to-End Service</p>
			<Route size={150} />
			<p>Experience seamless installation and setup at your location, ensuring a fully operational product from the
				moment we complete the job.</p>
		</button>
		<Modal bind:showModal={showModalService}>
			{#snippet header()}
				End-to-End Service
			{/snippet}
			{#snippet children()}
				<Route size={100} />
				<p>Our end-to-end service ensures your IoT crop monitoring system is up and running with minimal effort on your
					part. From initial consultation to final setup, our expert team handles everything—site assessment, hardware
					installation, software configuration, and system testing. We provide on-site training to ensure your team is
					confident in using the system. Post-installation, our dedicated support team is available 24/7 to address any
					questions or issues, guaranteeing a hassle-free experience and a fully operational solution tailored to your
					farm's unique needs.</p>
				<img src="https://images.unsplash.com/photo-1581091226825-a6a2a5aee158" alt="Technician working on equipment for end-to-end service" class="mt-4 w-full h-auto rounded-xl" />
			{/snippet}
		</Modal>
		<button onclick={() =>(showModalHardware = true)}
						class="bg-emerald-900 text-white lg:w-1/3 lg:h-[45rem] text-center items-center rounded-md lg:rounded-none flex flex-col justify-center space-y-12 lg:space-y-20 py-20 px-8 hover:-translate-y-10 transition ease-in-out">
			<p class="text-4xl font-semibold">Long Lasting Hardware</p>
			<Shield size={150} />
			<p>Benefit from durable, high-quality hardware built to withstand the test of time, minimizing maintenance and
				ensuring reliable performance.</p>
		</button>
		<Modal bind:showModal={showModalHardware}>
			{#snippet header()}
				Long Lasting Hardware
			{/snippet}
			{#snippet children()}
				<Shield size={100} />
				<p>Our IoT devices are engineered for durability and reliability in the harshest agricultural environments.
					Constructed with weather-resistant materials, our sensors and monitoring equipment are designed to endure
					extreme temperatures, moisture, and dust, ensuring consistent performance year-round. With a focus on
					longevity, our hardware requires minimal maintenance, reducing downtime and operational costs. Each device
					undergoes rigorous testing to meet the highest quality standards, providing you with a dependable solution
					that supports your farm’s productivity for years to come.</p>
				<img src="https://images.unsplash.com/photo-1516321497487-e288fb19713f" alt="Close-up of durable IoT hardware components" class="mt-4 w-full h-auto rounded-xl" />
			{/snippet}
		</Modal>
		<button onclick={() =>(showModalCoverage = true)}
						class="bg-green-500 text-white lg:w-1/3 lg:h-[45rem] lg:rounded-r-xl lg:rounded-none rounded-md text-center items-center flex flex-col justify-center space-y-12 lg:space-y-20 py-20 px-8 hover:-translate-y-10 transition ease-in-out">
			<p class="text-4xl font-semibold">The Best Signal Coverage</p>
			<RadioTower size={150} />
			<p>Achieve superior connectivity with our advanced systems, delivering unmatched signal coverage and powered by
				long-lasting, low-maintenance batteries.</p>
		</button>
		<Modal bind:showModal={showModalCoverage}>
			{#snippet header()}
				The Best Signal Coverage
			{/snippet}
			{#snippet children()}
				<RadioTower size={100} />
				<p>Our IoT crop monitoring systems leverage cutting-edge connectivity technology to ensure seamless data
					transmission across your entire farm, no matter the size or terrain. With advanced signal amplification and
					low-power wide-area network (LPWAN) technology, our devices provide unmatched coverage, even in remote or
					challenging environments. Powered by long-lasting, low-maintenance batteries, our systems minimize the need
					for frequent replacements, ensuring continuous monitoring and real-time insights into soil health, moisture
					levels, and crop conditions, all accessible from your smartphone or computer.</p>
				<img src="https://images.unsplash.com/photo-1548244250-9aa08b58f204?q=80&w=2340&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" alt="Radio tower ensuring superior signal coverage" class="mt-4 w-full h-auto rounded-xl" />
			{/snippet}
		</Modal>
	</div>
</section>

<!-- Products Quickview Section -->
<!-- <section id="products-quickview" class="bg-gray-600 py-10 text-white">
	<div class="container mx-auto text-center">
		<h2 class="text-3xl font-bold">{m.home_popular_products_title()}</h2>
		<p class="mt-4">
			{m.home_popular_products_subtitle()}<a href="#"><u>click here</u></a>.
		</p>
	</div>
	<LineCarasol />
</section> -->

<!-- Pricing Section -->
<section id="pricing" class="bg-gradient-to-t from-white to-[#cfecff]  py-20 px-4">
	<div class="container mx-auto text-center">
		<h2 class="text-3xl font-bold lg:text-5xl">{m.home_pricing_title()}</h2>
		<p class="mt-4 font-light py-6 lg:text-2xl">{m.home_pricing_subtitle()}</p>
		<div class="mt-10 grid grid-cols-1 gap-8 md:grid-cols-2">
			<PriceCard
				title="IoT"
				description={m.price_1()}
				features={languageTag() == 'ja'
					? [
							'データ2年分保存（データベース）',
							'データの一元管理（アプリケーションサーバー）',
							'LoRaWANサーバー',
							'アラート通知※1',
							'データダウンロード',
							'レポート作成・自動配信',
							'権限付与',
							'無制限ログイン',
							'APIアクセス'
						]
					: [
							'Store data for 2 years (database)',
							'Centralized data management (application server)',
							'LoRaWAN Server',
							'Alert notifications*1',
							'Data download',
							'Report generation and automatic distribution',
							'Permission granting',
							'Unlimited logins',
							'API access'
						]}
				link="#"
				color="bg-green-500"
				buttonLabel={m.home_pricing_get_started()}
			/>

			<PriceCard
				title={m.home_pricing_volume_agreement()}
				description={m.price_3()}
				features={languageTag() == 'ja'
					? [
							'大量のデバイスに関する交渉',
							'第三者流通契約',
							'デバイス＆ゲートウェイのレンタルパッケージ',
							'パートナーシップと協業',
							'単発プロジェクトおよび実験',
							'カスタマイズされたソリューション',
							'優先サポート',
							'カスタムSLA'
						]
					: [
							'Negotiate on large amounts of devices',
							'3rd part distribution agreements',
							'Device & gateway rental bundles',
							'Partnerships & collaborations',
							'One-off projects and experiments',
							'Customized solutions',
							'Priority support',
							'Custom SLA'
						]}
				link="/contact-us"
				color="bg-yellow-300"
				buttonLabel={m.home_pricing_contact_us_options()}
			/>
		</div>
	</div>
	<p class="p-6">{m.home_pricing_disclaimer_1()}</p>
</section>

<!-- Contact Section -->
<section id="contact" class="bg-gray-100 py-20">
	<div class="container mx-auto text-center">
		<h2 class="text-3xl font-bold">{m.home_contact_title()}</h2>
		<p class="mt-4">{m.home_contact_subtitle()}</p>
		<a
			class="mt-6 inline-block rounded bg-blue-600 px-4 py-2 text-white transition hover:bg-blue-700"
			href="contact-us">{m.contact_us()}</a
		>
	</div>
</section>

<!-- Remarks on Asterisk Section -->
<section id="remarks" class="flex flex-col bg-gray-200 py-10 pl-3 text-left">
	<ol>
		<li>
			<sm>※1</sm>
			{m.home_disclaimer_1()}
			<a class="cursor-pointer font-bold text-blue-900 underline" href="https://discord.com/"
			>Discord</a
			>
		</li>
	</ol>
</section>
