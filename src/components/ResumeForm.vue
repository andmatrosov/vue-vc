<template>
	<form class="card card-w30" @submit.prevent="createBlock">

		<app-select
				label="Тип блока"
				name="block-type"
				:options="selectOption"
				:value="formType"
				@selectChanged="selectFieldChanged"
		></app-select>

		<app-textarea
				name="value"
				label="Значение"
				:value="formText"
				@textAreaChanged="textAreaFieldChanged"
		></app-textarea>

		<app-button
				type="submit"
				text="Добавить"
				color="primary"
				:disabled="formText.length < 3"
		></app-button>

	</form>
</template>

<script>
import AppSelect from "@/components/AppSelect.vue";
import AppTextarea from "@/components/AppTextarea.vue";
import AppButton from "@/components/AppButton.vue";

export default {
	components: { AppSelect, AppTextarea, AppButton },
	emits: ['createBlock'],
	data() {
		return {
			formType: 'title',
			formText: '',
			selectOption: [
				{
					name: 'Заголовок',
					value: 'title'
				},
				{
					name: 'Подзаголовок',
					value: 'subtitle'
				},
				{
					name: 'Аватар',
					value: 'avatar'
				},
				{
					name: 'Текст',
					value: 'text'
				}
			]
		}
	},
	methods: {
		selectFieldChanged(value) {
			this.formType = value;
		},
		textAreaFieldChanged(value) {
			this.formText = value;
		},
		createBlock() {
			console.log(`Блок типа ${this.formType} создан со значением ${this.formText}`);
			this.$emit('createBlock', {type: this.formType, value: this.formText});
			this.formType = 'title'
			this.formText = '';
		}
	}
}
</script>

<style lang="scss" scoped>

</style>