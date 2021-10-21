<template>
	<div id="app">
		<div class="container-app">
			<div class="container-quiz">
				<div class="quiz-header"><h1>Quiz</h1></div>

				<div class="quiz-main" v-for="(element, index) in questions.slice(a, b)" :key="index" v-show="quiz">
					<div class="box-question">
						<h2 class="box-question-question">Question {{ b }}/{{ questions.length }}</h2>
						<p>{{ element.question }}</p>
					</div>
					<div class="box-suggestions">
						<ul>
							<!-- 判斷select變數是否為true -->
							<li v-for="(item, index) in element.suggestions" :key="index" :class="select ? check(item) : ''" @click="selectResponse(item)">
								{{ item.suggestion }}
								<div class="fas fa-check" v-if="select? item.correct:''"></div>
								<div class="fas fa-times" v-if="select? !item.correct:''"></div>
							</li>
						</ul>
					</div>
				</div>

				<div class="box-score" v-show="showScore">
					<h2>Your score is</h2>
					<h2>{{ score }}/{{ questions.length }}</h2>
					<div class="btn-restart">
						<button @click="restartQuiz"> Restart <i class="fas fa-sync-alt"></i></button>
					</div>
				</div>
				<div class="quiz-footer">
					<div class="box-button">
						<button type="button" @click="skipQuestion()" :style="!this.next?'background-color:rgb(10,128,202)':''">Skip</button>
						<button type="button" @click="nextQuestion()" :style="this.next?'background-color:rgb(10,128,202)':''">Next</button>
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
	data() {
		return {
			questions: [
				{
					question: 'One day Tony ___ to the store to see Mary',
					suggestions: [{ suggestion: 'go' }, { suggestion: 'went', correct: true }, { suggestion: 'going' }, { suggestion: 'is go' }]
				},
				{
					question: 'The man ___ got black hair and glasses',
					suggestions: [{ suggestion: 'have' }, { suggestion: 'has', correct: true }, { suggestion: 'is' }, { suggestion: 'had' }]
				},
				{
					question: '___ you like to go out tomorrow',
					suggestions: [{ suggestion: 'Will' }, { suggestion: 'Would', correct: true }, { suggestion: 'Are' }, { suggestion: 'Is' }]
				},
				{
					question: "___'s the weather like in New York?",
					suggestions: [{ suggestion: 'Is' }, { suggestion: 'Will' }, { suggestion: 'When' }, { suggestion: 'What', correct: true }]
				},
				{
					question: 'I just ___ from college last year',
					suggestions: [{ suggestion: 'graduate' }, { suggestion: 'graduated', correct: true }, { suggestion: 'will graduate' }, { suggestion: 'am graduated' }]
				}
			],
			a: 0,
			b: 1,
			select: false,
			score: 0,
			showScore: false,
			quiz: true,
			next:false,
		};
	},
	methods: {
		selectResponse(item) {
			this.select = true;
			this.next = true;
			if (item.correct) return this.score++;
		},
		check(status) {
			if (status.correct) return 'correct';
			return 'incorrect';
		},
		nextQuestion() {
			if (!this.next) return;
			if (this.questions.length - 1 == this.a) {
				this.showScore = true;
				this.quiz = false;
			} else {
				this.a++, this.b++, (this.select = false),(this.next = false);
			}
			
		},
		skipQuestion(){
			if (this.next) return;
			if (this.questions.length - 1 == this.a){
				this.showScore = true;
				this.quiz = false;
			}else{
				this.a++,this.b++
			}
		},
		restartQuiz(){
			//重置data
			//this.$data訪問現在的虛擬DOM  this.$options.data() 訪問初始的data值
			//Object.assign (target, ...sources) 【target：目標對象】，【souce：資料初始值】
			Object.assign(this.$data,this.$options.data())
		}
	}
};
</script>

<style>
#app {
}
</style>
