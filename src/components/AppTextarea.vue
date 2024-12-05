<template>
	<div class="form-control">
		<label :for="fieldId">{{ label }}</label>
		<textarea :name="name" :id="fieldId" rows="3" @input="textAreaChanged" v-model="textValue"></textarea>
	</div>
</template>

<script>
export default {
	props: ['label', 'name', 'value'],
	data() {
		return {
			textValue: this.$props.value
		}
	},
	watch: {
		value: {
			immediate: true,
			handler(newVal, oldVal) {
				this.textValue = newVal;
			}
		}
	},
	methods: {
		fieldId() {
			return this.name + '-' + Math.random();
		},
		textAreaChanged(e) {
			this.$emit('textAreaChanged', e.target.value);
		}
	}
}
</script>

<style lang="scss" scoped>

</style>