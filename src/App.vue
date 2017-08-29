<template>
	<div>
		<LayoutHeader></LayoutHeader>
		<div ref="layoutWrapper" class="layoutWrapper">
			<div ref="layoutMain">
				<router-view></router-view>
			</div>
			<LayoutFooter></LayoutFooter>
		</div>
	</div>
</template>

<script>
import LayoutHeader from "@/components/LayoutHeader"
import LayoutFooter from "@/components/LayoutFooter";

export default {
	name: 'app',
	data () {
		return {
			headerHeight: 64
		}
	},
	components: {
		LayoutHeader,
		LayoutFooter
	},
	mounted () {
		this.wrapperInit();
		window.onresize = this.wrapperInit;
	},
	methods: {
		getHeight () {
			return document.documentElement.clientHeight;
		},
		wrapperInit () {
			let height = this.getHeight();
			let layoutWrapper = this.$refs.layoutWrapper;
			let wrapperHeight = parseFloat(height - this.headerHeight);
			let layoutMain = this.$refs.layoutMain;
			let mainHeight = parseFloat(wrapperHeight - this.headerHeight);

			layoutWrapper.style.height = wrapperHeight + "px";
			layoutMain.style.minHeight = mainHeight + "px";
		}
	}
}
</script>

<style scoped>
.layoutWrapper {
	overflow: auto;
}
</style>
