<template>
	<div class="grade-entry" v-bind:class="{fixed_grade_entry: fixed_grade_entry}" id="grade-entry">
		<div class="columns">
			<div class="column">
			  	<label class="label">Number of Questions</label>
			  	<p class="control">
					<input class="input is-primary" type="number" placeholder="Number of questions" v-model="c_number_of_questions" v-on:change="gradeEntryChange">
				</p>
			</div>
			<div class="column">
			  	<label class="label">Out Of</label>
			  	<p class="control">
					<input class="input is-info" type="number" placeholder="Out Of" v-model="c_out_of" v-on:change="gradeEntryChange">
				</p>
			</div>
		</div>

	</div>
</template>

<script>
export default {
	data() {
		return {
			c_number_of_questions:this.number_of_questions,
			c_out_of:this.out_of,
		}
	},
	props:['number_of_questions', 'out_of', 'fixed_grade_entry'],
	methods: {
		gradeEntryChange : function(){
			this.$emit('gradeEntryChange', { number_of_questions:this.c_number_of_questions, out_of:this.c_out_of})
		},
	}
}

</script>

<style scoped>
	.fixed_grade_entry{
		position: fixed;
	    width: 100%;
	    top: 0;
	    z-index: 999;
	    background: whitesmoke;
	    padding: 2.5em 2em;
	    margin: -1em;
	    max-width:1200px;
	    border-bottom:1px solid #00d1b2;
	}
</style>
