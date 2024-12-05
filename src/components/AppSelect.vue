<template>
	<div class="form-control">
		<label for="fieldId">{{ label }}</label>
		<select :name="name" :id="fieldId" v-model="selectValue" @change="selectChanged">
			<option v-for="(option, idx) in options" :value="option.value" :selected="idx === 0">{{ option.name }}</option>
		</select>
	</div>
</template>

<script>
export default {
	props: ['label', 'value', 'name', 'options'],
	emits: ['selectChanged'],
	data() {
		return {
			selectValue: this.$props.value
		}
	},
	watch: {
		value:{
			immediate: true,
			handler(newVal, oldVal) {
				this.selectValue = newVal
			}
		}
	},
	computed: {
		fieldId() {
			return this.name + '-' + Math.random();
		},
	},
	methods: {
		selectChanged(e) {
			this.$emit('selectChanged', this.selectValue);
		}
	}
}
</script>

<style lang="scss" scoped>

</style>