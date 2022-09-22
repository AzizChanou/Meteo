<template>
	<NavBar />
	<ScanHome />
	<FootBar />
</template>

<script>
import Preload from "../views/Preload.vue";
import PageNotFound from "../views/PageNotFound.vue";
import NavBar from "../components/NavBar.vue";
import FootBar from "../components/FootBar.vue";
import ScanHome from "../views/ScanHome.vue";

export default {
	name: "App",
	components: {
		Preload,
		NavBar,
		FootBar,
		ScanHome,
		PageNotFound,
	},
};
</script>