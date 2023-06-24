<script lang="ts">
	import { onMount } from 'svelte';
	import { fade } from 'svelte/transition';
	import * as THREE from 'three';

	let titleVisible = false;

	onMount(() => {
		titleVisible = true;

		const canvas = document.getElementById('canvas');

		const height = canvas?.offsetHeight || 0;
		const width = canvas?.offsetWidth || 0;

		const scene = new THREE.Scene();

		const camera = new THREE.PerspectiveCamera(75, width / height);
		camera.position.set(0, 0, 10);

		const renderer = new THREE.WebGLRenderer();
		renderer.setSize(width, height);
		canvas?.appendChild(renderer.domElement);

		renderer.render(scene, camera);
	});
</script>

<div class="w-screen h-screen bg-stone-950 flex justify-around items-center relative">
	{#if titleVisible}
		<div
			transition:fade={{ delay: 200, duration: 1300 }}
			class="absolute self-center text-6xl opacity-75 text-transparent bg-clip-text bg-gradient-to-r from-gray-500 to-slate-400 top-5"
		>
			SMOKE
		</div>
	{/if}
	<div id="canvas" class="h-[500px] w-[900px] bg-white opacity-75 rounded-lg drop-shadow-2xl" />
</div>
