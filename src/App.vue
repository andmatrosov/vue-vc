<template>
  <div class="container column">
		<resume-form @createBlock="saveBlock"></resume-form>

    <resume-view :elements="blocksArray"></resume-view>
  </div>

	<resume-comments @load="loadComments" :comments="comments"></resume-comments>
</template>

<script>
import ResumeForm from "@/components/ResumeForm.vue";
import ResumeView from "@/components/ResumeView.vue"
import ResumeComments from "@/components/ResumeComments.vue"
import axios from "axios";

export default {
	components: { ResumeForm, ResumeView, ResumeComments },
	data() {
		return {
			blocksArray: [],
			comments: [],
		}
	},
	methods: {
		saveBlock(obj) {
			this.blocksArray.push(obj);
		},
		async loadComments() {
			const { data } = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42');
			console.log(data)
			this.comments = [...data]
		}
	}
}
</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>
