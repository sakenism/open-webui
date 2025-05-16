<script lang="ts">
	import { onMount, getContext } from 'svelte';
	import { WEBUI_NAME, config, settings } from '$lib/stores';
	import Modal from './common/Modal.svelte';
	import { updateUserSettings } from '$lib/apis/users';

	const i18n = getContext('i18n');

	export let show = false;
	export let onAccept = () => {};

	let agreementAccepted = false;
</script>

<Modal bind:show size="lg">
	<div class="px-5 pt-4 dark:text-gray-300 text-gray-700">
		<div class="flex justify-between items-start">
			<div class="text-xl font-semibold">
				{$i18n.t('User Agreement')}
			</div>
			<button
				class="self-center"
				on:click={() => {
					show = false;
				}}
			>
				<svg
					xmlns="http://www.w3.org/2000/svg"
					viewBox="0 0 20 20"
					fill="currentColor"
					class="w-5 h-5"
				>
					<path
						d="M6.28 5.22a.75.75 0 00-1.06 1.06L8.94 10l-3.72 3.72a.75.75 0 101.06 1.06L10 11.06l3.72 3.72a.75.75 0 101.06-1.06L11.06 10l3.72-3.72a.75.75 0 00-1.06-1.06L10 8.94 6.28 5.22z"
					/>
				</svg>
			</button>
		</div>
	</div>

	<div class="w-full p-4 px-5 text-gray-700 dark:text-gray-100">
		<div
			class="overflow-y-scroll max-h-96 scrollbar-hidden border dark:border-gray-700 p-3 rounded text-sm leading-6 space-y-3"
		>
			<p>
				<span class="font-bold text-lg">{$i18n.t('Dear user!')}</span>
			</p>
			<p>
				{$i18n.t(
					'As part of the integration of artificial intelligence technologies into work processes, please note the strict necessity to comply with information security requirements under the legislation of the Republic of Kazakhstan in this area, as well as regulatory legal acts approved by the Office of the Government of the Republic of Kazakhstan.'
				)}
			</p>
			<p class="font-bold">{$i18n.t('Please note when using AI:')}</p>
			<ul class="list-disc list-inside mb-3">
				<li>
					<span class="font-bold">{$i18n.t('It is prohibited to transmit')}</span>
					{$i18n.t(' confidential, official, or personal information to AI systems.')}
				</li>
				<li>
					{$i18n.t(
						'All actions must comply with regulatory acts on information security and legislation, including the Law of the Republic of Kazakhstan "On Personal Data and Their Protection".'
					)}
				</li>
			</ul>
			<p>
				<span class="font-bold"
					>{$i18n.t('Responsibility for compliance with these standards')}</span
				>
				{$i18n.t(' lies with each employee using AI in their professional activities.')}
			</p>
			<p>
				<span class="text-yellow-500 text-lg">🔔</span>
				<span class="text-gray-900 dark:text-gray-100">
					{$i18n.t(
						'Failure to comply with established requirements may result in disciplinary, administrative, and in some cases, criminal liability in accordance with applicable law.'
					)}
				</span>
			</p>
		</div>
	</div>
</Modal>
