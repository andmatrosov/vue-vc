<template>
	<div class="container">
		<p>
			<button v-if="comments.length === 0"  class="btn primary" @click="loadComments">Загрузить комментарии</button>
		</p>
		<div class="card" v-if="comments.length !== 0 && loading === false">
			<h2>Комментарии</h2>
			<ul class="list">
				<li class="list-item" v-for="comment in comments" :key="comment.id">
					<div>
						<p><strong>{{ comment.email }}</strong></p>
						<small>{{ comment.body }}</small>
					</div>
				</li>
			</ul>
		</div>
		<div class="loader" v-else-if="loading === true"></div>
	</div>
</template>

<script>
export default {
	props: ['comments'],
	emits: ['load'],
	data() {
		return {
			loading: false,
			commentsArray: this.$props.comments
		}
	},
	watch: {
		comments: {
			immediate: true,
			handler(newVal, oldVal) {
				this.commentsArray = newVal;
				this.loading = false;
			}
		}
	},
	methods: {
		loadComments() {
			this.loading = true
			this.$emit('load');
		}
	}
}
</script>

<style lang="scss" scoped>

</style>