<template>
	<button class="btn" :class="color" :type="type" @click="$emit('clickBtn')" :disabled>{{ text }}</button>
</template>

<script>
export default {
	props: ['type', 'text', 'color', 'disabled'],
	emits: ['clickBtn'],
}
</script>

<style lang="scss" scoped>

</style>