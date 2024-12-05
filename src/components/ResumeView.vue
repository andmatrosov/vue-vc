<template>
	<div class="card card-w70">
		<h3 v-if="elements.length === 0">Добавьте первый блок, чтобы увидеть результат</h3>

		<component v-for="element in elements" :is="`resume-${element.type}`" :value="element.value" :key="element.value"></component>

	</div>
</template>

<script>
import ResumeAvatar from "@/components/parts/ResumeAvatar.vue";
import ResumeTitle from "@/components/parts/ResumeTitle.vue";
import ResumeSubtitle from "@/components/parts/ResumeSubtitle.vue";
import ResumeText from "@/components/parts/ResumeText.vue";

export default {
	components: { ResumeAvatar, ResumeTitle, ResumeSubtitle, ResumeText },
	props: {
		elements: {
			type: Array,
			required: true
		}
	}
}
</script>

<style lang="scss" scoped>
</style>