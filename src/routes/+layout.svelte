<!-- *HTML -->
<div class="background">
	<h1 class="mainTitle">SalesSystem</h1>
</div>

<slot />

<!-- *Style -->
<style>
	.background {
		background-color: var(--main-color);
		display: flex;
		align-items: center;
		justify-content: center;
		position: absolute;
		left: 0;
		top: 0;
		width: 100vw;
		height: 100vh;
		text-align: center;
		z-index: -1;
	}
	.mainTitle {
		color: rgba(255, 255, 255, 0.5);
		font-size: 6rem;
		text-align: center;
		padding: 5px;
	}
</style>
