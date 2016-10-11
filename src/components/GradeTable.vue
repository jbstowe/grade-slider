<template>
	<div class="grade-table">
		<hr>
		<table class="table is-striped is-bordered"> 
			<thead> 
				<tr> 
					<th>Number Missed</th> 
					<th>Grade (rounded up)</th> 
					<th>Grade</th> 
				</tr> 
			</thead> 
			<tbody v-for="n in gradeRange"> 
				<tr> 
					<th scope="row">{{ n }}</th> 
					<td> {{ Math.round(calcGrade(n)) }}</td> 
					<td> {{ parseFloat(calcGrade(n).toFixed(5)) }}</td> 
				</tr> 
			</tbody>
		</table>
	</div>
	
</template>

<script>
import _ from 'underscore'

export default {
	props:['number_of_questions', 'out_of'],
	computed: {
		gradeRange: function() {
			return _.range(0, (this.number_of_questions + 1));
		}
	},
	methods: {
		calcGrade: function(n) {
			return this.out_of * ((this.number_of_questions-n)/this.number_of_questions);
		}
	}
}
</script>

<style></style>
