<script lang="ts">
    import { onMount } from 'svelte';

	let canvas: HTMLCanvasElement | undefined
	let context: CanvasRenderingContext2D
	let imageData: ImageData
	$: if (canvas) {
		context = canvas.getContext('2d')!
		const img = new Image()
		img.src = './kronii.png'
		img.onload = () => {
			let centerPointOfCanvas = [canvas!.width / 2, canvas!.height / 2]
			// Scale the image down
			
			let ratio = img.width / img.height
			let newScale = Math.min(canvas!.height / Math.max(img.height, img.width), 1)
			let newLength:number = 0
			let newImageSize:number[] = []

			if (img.height > img.width) {
				newLength = img.height * newScale
				newImageSize = [ratio * newLength,newLength]
			} else {
				newLength = img.width * newScale
				newImageSize = [newLength, ratio * newLength]
			}


			console.log(`${img.width} ${img.height} ${centerPointOfCanvas[0] - newImageSize[0] / 2} ${centerPointOfCanvas[1] - newImageSize[1] / 2} ${newImageSize[0]} ${newImageSize[1]}`)

			// Draw the image
			context.drawImage(img,0,0, img.width, img.height,  centerPointOfCanvas[0] - newImageSize[0] / 2,  centerPointOfCanvas[1] - newImageSize[1] / 2, newImageSize[0], newImageSize[1])

			imageData = context.getImageData(0,0,newImageSize[0], newImageSize[1])
		}
	}

	onMount( () => {
		console.log(canvas)
	})

</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>


	<img src="ina.png" width="200" height="200" alt="ina" />
	<canvas width="500" height="500" bind:this={canvas} />
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}


</style>
