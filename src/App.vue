<template>
	<div id="app">
		<div class="container-app">
			<div class="container-quiz">
				<div class="quiz-header">
					<h1>Quiz</h1>
				</div>

				<div class="quiz-main" v-for="(element,index) in questions.slice(a,b)" :key="index">
					<div class="box-question">
						<h2 class="box-question-question">Question {{b}}/{{questions.length}} </h2>
						<p>{{element.question}}</p>
					</div>
					<div class="box-suggestions">
						<ul>
							<!-- 判斷select變數是否為true -->
							<li v-for="(item,index) in element.suggestions" :key="index" :class="select? check(item):''" @click="selectResponse(item)">{{item.suggestion}}</li>
						</ul>
					</div>
				</div>
				
				<div class="box-score">
					<h2>Your score is</h2>
					<h2>{{score}}/{{questions.length}}</h2>
				</div>
				<div class="quiz-footer">
					<div class="box-button">
						<button type="button">Skip</button>
						<button type="button" @click="nextQuestion()">Next</button>
					</div>
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
			],
			a:0,
			b:1,
			select:false,
			score:0,
		}
	},
	methods:{
		selectResponse(item){
			this.select = true;
			if (item.correct) return this.score++
		},
		check(status){
			if(status.correct) return "correct";
			return "incorrect"
		},
		nextQuestion(){
			this.a++,
			this.b++,
			this.select = false
		}
	}
};
</script>

<style>
#app {
	
}
</style>
