<template>
	<div id="app">
		<div class="container-app">
			<div class="container-quiz">
				<div class="quiz-header">
					<h1>Quiz</h1>
				</div>

				<div class="quiz-main" v-for="(element,index) in questions" :key="index">
					<div class="box-question">
						<h2>Question</h2>
						<p>{{element.question}}</p>
					</div>
					<div class="box-suggestions" v-for="(item,index) in element.suggestions" :key="index">
						<ul>
							<li>{{item.suggestion}}</li>
						</ul>
					</div>
				</div>
				
				<div class="box-score">
					score
				</div>
				<div class="quiz-footer">
					<h1>footer</h1>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'App',
	components: {},
	data(){
		return{
			questions:[
				{
					question:"One day Tony ___ to the store to see Mary",
					suggestions:[
						{suggestion:"go",correct:true},
						{suggestion:"went"},
						{suggestion:"going"},
						{suggestion:"is go"}
					]
				},
				{
					question:"The man ___ got black hair and glasses",
					suggestions:[
						{suggestion:"have"},
						{suggestion:"has",correct:true},
						{suggestion:"is"},
						{suggestion:"had"}
					]
				},
				{
					question:"___ you like to go out tomorrow",
					suggestions:[
						{suggestion:"Will"},
						{suggestion:"Would",correct:true},
						{suggestion:"Are"},
						{suggestion:"Is"}
					]
				},
				{
					question:"___'s the weather like in New York?",
					suggestions:[
						{suggestion:"Is"},
						{suggestion:"Will"},
						{suggestion:"When"},
						{suggestion:"What",correct:true}
					]
				},
				{
					question:"I just ___ from college last year",
					suggestions:[
						{suggestion:"graduate"},
						{suggestion:"graduated",correct:true},
						{suggestion:"will graduate"},
						{suggestion:"am graduated"}
					]
				}
			]
		}
	}
};
</script>

<style>
#app {
	
}
</style>
