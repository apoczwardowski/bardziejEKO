<template>
	<section id="quiz">
		<div class="quiz-header">
			<h2>?</h2>
			<h1>Wypełnij ankietę i zobacz jakie odpowiedzi zaznaczyła większość</h1>
		</div>
		<section class="menu">
			<div class="card">
				<div class="image">
					<div class="bg"></div>
					<img src="@/assets/images/quizLogo.svg">
				</div>
				<a href="https://forms.gle/fhRAbAUxsQArdVz77" target="blank" class="btn b-quiz" @click="isResultsVisible = !isResultsVisible">Przejdź do quizu!</a>
			</div>
			<div class="card">
				<div class="image">
					<img src="@/assets/images/resultsLogo.svg">
				</div>
				<button class="btn" @click="isResultsVisible = !isResultsVisible">{{ isResultsVisible ? 'Schowaj': 'Rozwiń' }} wyniki</button>
			</div>
		</section>
		<section class="results" v-if="isResultsVisible">
			<h2>Wyniki ankiety</h2>
			<div class="ages">
				<button
					class="btn-age"
					@click="selectAge(age.value)"
					:class="{'active-age' : (selectedAge == age.value)}"
					v-for="(age, index) in ages"
					:key="index"
				>
					<p>{{ age.text }} {{ age.isRange ? 'lat' : '' }}</p>
				</button>
			</div>
			<div v-if="!isNoData" class="data">
				<div class="card"  v-for="(result, index) in results" :key="index">
					<div class="percentage">
						<span class="number">{{ result.percentage }}<span>%</span></span>
					</div>
					<p class="text">{{ result.title }}</p>
				</div>
			</div>
			<div v-if="isNoData" style='color: #f00; font-size: 1.5em'>Brak danych dla tej grupy wiekowej</div>
			<a href="#quiz" class="hiding">
				<button class="btn" @click="isResultsVisible = false">Schowaj wyniki</button>
			</a>
		</section>
	</section>
</template>

<script>
export default {
	name: 'Quiz',
	data() {
		return {
			isResultsVisible: false,
			selectedAge: 0,
			isNoData: false,
			ages: [
				{
					text: 'Wszyscy',
					value: 0,
					isRange: false
				},
				{
					text: '< 18',
					value: 'Poniżej 18 lat',
					isRange: true
				},
				{
					text: '18 - 29',
					value: '18 - 29',
					isRange: true
				},
				{
					text: '30 - 39',
					value: '30 - 39',
					isRange: true
				},
				{
					text: '40 - 49',
					value: '40 - 49',
					isRange: true
				},
				{
					text: '> 50',
					value: 'Powyżej 50 lat',
					isRange: true
				}
			],
			answers: [
				['Tak', 'Nie'],
				['W telewizji', 'W internecie', 'W gazecie', 'W szkole', 'Nie słyszałem/am nic na ten temat'],
				['Tak', 'Nie'],
				['Stały wzrost średniej temperatury powietrza na Ziemi obserwowany od kilkudziesięciu lat', 'Globalne ocieplenie stosunków międzynarodowych', 'Stały spadek średniej temperatury powietrza na Ziemi obserwowany od kilkudziesięciu lat', 'Takie pojęcie nie istnieje'],
				['Tak', 'Nie'],
				['Tak', 'Nie'],
				['Drzewa', 'Hodowle zwierząt gospodarskich', 'Nawozy azotowe', 'Emisja dwutlenku węgla'],
				['Palenie węglem w piecu', 'Przemieszczanie się rowerem zamiast samochodem osobowym', 'Zamiana ogrzewania węglowego na gazowe', 'Tworzenie ognisk na świeżym powietrzu'],
				['Działalność człowieka', 'Natura', 'Zwierzęta domowe', 'Działalność sprzętu komputerowego'],
				['Zjawisko podwyższenia temperatury planety przez obecne w jej atmosferze gazy cieplarniane', 'Takie pojęcie nie istnieje', 'Zjawisko podwyższenia temperatury ciała człowieka poprzez zbliżenie się do źródła ciepła', 'Zjawisko przegrzania się maszyny'],
				['Gazowy składnik atmosfery biorący udział w efekcie cieplarnianym', 'Gazy, dzięki którymi możemy oddychać', 'Takie pojęcie nie istnieje.', 'Gazy, które są często używane do ocieplania mieszkań'],
				['Globalne ocieplenie jest skutkiem efektu cieplarnianego', 'Wycinanie drzew jest niekorzystne dla klimatu', 'Ludzka dzialanosc na ziemii jest jedyną przyczyną globalnego ocieplenia', 'Zmiany klimatu naszej planety są Naturalne'],
				['Azot', 'Tlen', 'Hel', 'Metan']
			],
			allTitles: [
				["Zainteresowanych tematem globalnego ocieplenia", "Niezainteresowanych tematem globalnego ocieplenia"],
				['Ankietowani najczęściej słyszeli o globalnym ociepleniu w telewizji', 'Ankietowani najczęściej słyszeli o globalnym ociepleniu w internecie', 'Ankietowani najczęściej słyszeli o globalnym ociepleniu w gazecie', 'Ankietowani najczęściej słyszeli o globalnym ociepleniu w szkole', 'Nie słyszało na temat globalnego ocieplenia'],
				["Uważa, że zbyt rzadko porusza się temat globalnego ocieplenia", "Uważa, że wystarczająco często porusza się temat globalnego ocieplenia"],
				['"Globalne ocieplenie to stały wzrost średniej temperatury powietrza na Ziemi obserwowany od kilkudziesięciu lat"', '"Globalne ocieplenie to globalne ocieplenie stosunków międzynarodowych"', '"Globalne ocieplenie to stały spadek średniej temperatury powietrza na Ziemi obserwowany od kilkudziesięciu lat"', '"Globalne ocieplenie to takie pojęcie nie istnieje"'],
				["Uważa, że globalne ocieplenie jest problemem", "Uważa, że globalne ocieplenie nie jest problemem"],
				["Uważa, że ma wpływ na zmiany klimatu", "Uważa, że nie ma wpływu na zmiany klimatu"],
				['"Drzewa pomagają pochłaniać CO2"', '"Hodowle zwierząt gospodarskich pomaga pochłaniać CO2"', '"Nawozy azotowe pomagają pochłaniać CO2"', '"Emisja dwutlenku węgla pomaga pochłaniać CO2"'],
				['"Palenie węglem w piecu ogranicza emisję CO2"', '"Przemieszczanie się rowerem zamiast samochodem osobowym ogranicza emisję CO2"', '"Zamiana ogrzewania węglowego na gazowe ogranicza emisję CO2"', '"Tworzenie ognisk na świeżym powietrzu ogranicza emisję CO2"'],
				['"Działalność człowieka ma największy wpływ na zmiany klimatu"', '"Natura ma największy wpływ na zmiany klimatu"', '"Zwierzęta domowe mają największy wpływ na zmiany klimatu"', '"Działalność sprzętu komputerowego ma największy wpływ na zmiany klimatu"'],
				['"Zjawisko podwyższenia temperatury planety przez obecne w jej atmosferze gazy cieplarniane, to efekt cieplarniany"', 'Uważa, że efekt cieplarniany nie istnieje', '"Zjawisko podwyższenia temperatury ciała człowieka poprzez zbliżenie się do źródła ciepła, to efekt cieplarniany"', '"Zjawisko przegrzania się maszyny, to efekt cieplarniany"'],
				['Uważa, że gaz cieplarniany, to gazowy składnik atmosfery biorący udział w efekcie cieplarnianym', 'Uważa, że gazy cieplarniane, to gazy, dzięki którymi możemy oddychać', 'Uważa, że gazy cieplarniane nie istnieją', 'Uważa, że gazy cieplarniane, to Gazy, które są często używane do ocieplania mieszkań'],
				['Uważa, że globalne ocieplenie nie jest skutkiem efektu cieplarnianego', 'Uważa, że wycinanie drzew nie jest niekorzystne dla klimatu', 'Uważa, że ludzka dzialanosc na ziemii nie jest jedyną przyczyną globalnego ocieplenia', 'Uważa, że zmiany klimatu naszej planety nie są naturalne'],
				['Uważa, że azot, to gaz cieplarniany', 'Uważa, że tlen, to gaz cieplarniany', 'Uważa, że hel, to gaz cieplarniany', 'Uważa, że metan, to gaz cieplarniany']
			],
			results: []
		};
	},
	methods: {
		fetchData() {
			const SHEET_ID = '13LtBakSxnzbjf3QQf1PpWcG8KD-rMWIrY1h_hO6IS8A';
			const RANGE = 'A2:O500';
			const API_KEY = 'AIzaSyCrxhW3GYZr8icaEes9QObM9v5rSVnw4bE';
			const SHEET_LINK = `https://sheets.googleapis.com/v4/spreadsheets/${ SHEET_ID }/values/${ RANGE }?key=${ API_KEY }`;

			const answers = this.answers;
			const allTitles = this.allTitles;

			// amount of answers as matrix
			const amount = [
				[0, 0],
				[0, 0, 0, 0, 0],
				[0, 0],
				[0, 0, 0, 0],
				[0, 0],
				[0, 0],
				[0, 0, 0, 0],
				[0, 0, 0, 0],
				[0, 0, 0, 0],
				[0, 0, 0, 0],
				[0, 0, 0, 0],
				[0, 0, 0, 0],
				[0, 0, 0, 0]
			];

			// fetching and composing data from API
			const processData = async () => {
				let raw = [];	// raw data
				let val = [];	// end result
				let temp = [];

				// fetching data
				const response = await fetch(SHEET_LINK);
				raw = (await response.json()).values;

				this.isNoData = true;

				// sorting data by age
				raw.forEach(e => {
					if (this.selectedAge === 0) {
						temp.push(e);
						this.isNoData = false;
					}
					else if ((e[1] == this.selectedAge) && (this.selectedAge !== 0)) {
						temp.push(e);
						this.isNoData = false;
					}

				});

				if(!this.isNoData) {
					raw = temp;

					// composing data
					for (let i = 1; i < raw[0].length; i++) {
						let temp = [];

						for (let j = 0; j < raw.length; j++)
							temp.push(raw[j][i]);

						val.push(temp);
					}

					// splitting and flatting data at 3rd question
					val[2].forEach((e, i) => val[2][i] = e.split(", "));
					val[2] = val[2].flat();

					return val;
				}
			}

			// making an array filled up of objects containing percentage and answers
			async function prepareResults(values) {
				let sums = [];			// sums of answers to each question
				let biggestNums = [];	// most popular answers
				let percents = [];		// all percents of the most popular answers as array
				let titles = [];		// titles of the most popular answers
				let results = [];		// end result

				// getting number of answers into matrix
				for (let i = 1; i < values.length; i++) {
					values[i].forEach(value => {
						answers[i - 1].forEach((answer, index) => {
							if(value == answer)
								amount[i - 1][index]++;
						});
					});
				}

				// getting sums of answers to each question
				amount.forEach((e, i) => {
					sums[i] = e.reduce((a, b) => a + b);
				});

				// filling up an array of amount of the most popular answers
				amount.forEach(e => biggestNums.push({
					number: Math.max(...e),
					index: e.indexOf(Math.max(...e))
				}));

				// making percentage from data
				sums.forEach((sum, i) => {
					let percent = (biggestNums[i].number * 100) / sum
					percents.push(percent);
				})

				// rounding percents
				percents = percents.map(a => Math.floor(a));

				// preparing titles based on data
				biggestNums.forEach((biggestNum, i) => {
					titles[i] = allTitles[i][biggestNum.index];
				});

				// creating array of results from processed data
				percents.forEach((percent, i) => {
					results.push({ percentage: percent, title: titles[i] });
				})

				return results;
			}

			// main function containing all needed functions
			const main = async () => {
				const processedData = await processData();

				if(!this.isNoData) {
					this.results = await prepareResults(processedData);
					this.isNoData = false;
				}
			}

			main();
		},
		selectAge(value) {
			this.selectedAge = value;
			this.fetchData();
		}
	},
	mounted() {
		this.fetchData();
	}
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/properties';
// $yellow;
// $light-green;
// $green;
// $dark-green;
// $padding-main;

// breakpoints
$tablets: 1200px;
$smartphones: 760px;

#quiz {
	padding: ($padding-main / 2) $padding-main;

	@media (max-width: $tablets) {
		padding: 5em 0;
	}

	.quiz-header {
		display: flex;
		justify-content: space-evenly;
		align-items: center;
		background: $green;
		margin-right: 6em;
		margin-bottom: 10em;
		width: 50vw;
		border-radius: 2.5vw;
		position: relative;
		transform: translateX(-50px);

		h1 {
			font-size: 2.5vw;
			padding: 2vw 5vw;
			color: $yellow;
		}

		h2 {
			position: absolute;
			display: flex;
			justify-content: center;
			align-items: center;
			width: 6vw;
			height: 6vw;
			left: 45vw;
			font-size: 3vw;
			background: $light-green;
			color: $dark-green;
			border-radius: 100vw;
			transform: translateY(100%);
		}
	}

	@media (max-width: $tablets) {
		.quiz-header {
			margin-right: 0em;
			width: 70vw;
			text-align: center;
			left: 50%;
			transform: translateX(-50%);
			margin-bottom: 8em;

			h1 {
				font-size: 4.5vw;
				padding: 2vw 4vw 2vw 4vw;
			}

			h2 {
				width: 10vw;
				height: 10vw;
				left: 30vw;
				bottom: 20px;
				font-size: 6.5vw;
				transform: translateY(110%);
			}
		}
	}

	@media (max-width: $smartphones) {
		.quiz-header {
			width: 85vw;
			text-align: center;

			h1 {
				font-size: 6.5vw;
				padding: 2vw 2vw 4vw 2vw;
			}

			h2 {
				width: 15vw;
				height: 15vw;
				left: 35vw;
				font-size: 8.5vw;
				transform: translateY(105%);
			}
		}
	}

	.menu {
		margin-bottom: 8em;
		position: relative;
		display: flex;
		justify-content: space-around;

		@media (max-width: $tablets) {
			margin-bottom: 6em;
			justify-content: space-around;
		}

		@media (max-width: $smartphones) {
			margin-bottom: 1em;
			flex-direction: column;
		}

		.card {
			display: flex;
			flex-direction: column;
			align-items: center;

			@media (max-width: $smartphones) {
				margin-bottom: 5em;
			}

			.image {
				height: 250px;
				width: 250px;
				background: $light-green;
				border-radius: 1000px;

				@media (max-width: $tablets) {
					height: 175px;
					width: 175px;
				}

				img {
					height: 105%;
					position: relative;
					top: 50%;
					left: 50%;
					transform: translate(-50%, -50%);
				}
			}

			.btn {
				width: 400px;
				color: $dark-green;
				background: none;
				border: $dark-green 5px solid;
				border-radius: 1000px;
				margin-top: 60px;
				padding: .5em;
				font-size: 2em;
				font-weight: 400;
				letter-spacing: 1px;
				cursor: pointer;

				@media (max-width: $tablets) {
					width: 300px;
					margin-top: 40px;
					font-size: 1.75em;
				}

				&:hover {
					color: $yellow;
					background: $green;
					border-color: $green;
				}
			}

			.b-quiz {
				display: block;
				color: $yellow;
				background: $dark-green;
				text-decoration: none;
				text-align: center;
			}
		}
	}

	.results {
		min-width: 880px;
		max-width: 1200px;
		padding: 2em 4vw;
		border: $dark-green 7px solid;
		border-radius: 50px;
		position: relative;
		left: 50%;
		transform: translateX(-50%);
		display: flex;
		flex-direction: column;
		align-items: center;

		@media (max-width: $tablets) {
			min-width: 0;
			max-width: 90vw;
			padding: 2em 4vw;
		}

		@media (max-width: $smartphones) {
			max-width: 95vw;
		}

		h2 {
			color: $dark-green;
			font-size: 2.75em;
			letter-spacing: 2px;
		}

		.ages {
			width: 100%;
			margin: 2em 0 5em 0;
			display: flex;
			justify-content: space-around;

			@media (max-width: $tablets) {
				margin: 1.5em 0 3em 0;
				flex-wrap: wrap;
			}

			.btn-age {
				width: 15%;
				color: $green;
				background: $yellow;
				border: $green 3px solid;
				padding: .35em;
				border-radius: 1000px;
				font-size: 1.5em;
				font-weight: 500;
				cursor: pointer;
				display: flex;
				justify-content: center;
				align-items: center;

				@media (max-width: $tablets) {
					width: 30%;
					margin-bottom: 1em;
					font-size: 1.25em;
				}

				@media (max-width: $smartphones) {
					width: 32%;
					flex-direction: column;
					font-size: 1em;
					padding: .5em .75em;
				}

				&:hover {
					color: $yellow;
					background: $green;
				}
			}

			.active-age {
				color: $yellow;
				background: $green
			}
		}

		.data {
			display: flex;
			flex-wrap: wrap;
			justify-content: space-between;

			.card {
				width: 45%;
				margin: 1em 0;
				display: flex;
				align-items: center;

				@media (max-width: $smartphones) {
					width: 90%;
				}

				.percentage {
					width: 100px;
					height: 100px;
					margin-right: 2em;
					color: $yellow;
					background: $green;
					border-radius: 1000px;

					@media (max-width: $tablets) {
						width: 80px;
						height: 80px;
					}

					.number {
						width: 75%;
						text-align: center;
						font-size: 2em;
						font-weight: 500;
						display: block;
						position: relative;
						top: 50%;
						left: 50%;
						transform: translate(-50%, -50%);

						@media (max-width: $tablets) {
							font-size: 1.5em;
						}

						span {
							font-weight: 300;
						}
					}
				}

				.text {
					width: 70%;
					color: $dark-green;
					font-size: 1.3em;
					font-weight: 600;
					letter-spacing: 1px;

					@media (max-width: $tablets) {
						width: 60%;
						font-size: 1em;
					}
				}
			}
		}

		.hiding {


			.btn {
				width: 300px;
				color: $yellow;
				background: $dark-green;
				border: $dark-green 3px solid;
				border-radius: 1000px;
				margin-top: 60px;
				padding: .5em;
				font-size: 1.5em;
				font-weight: 400;
				letter-spacing: 1px;
				cursor: pointer;

				@media (max-width: $tablets) {
					width: 250px;
					margin-top: 40px;
					font-size: 1.25em;
				}

				&:hover {
					color: $yellow;
					background: $green;
					border-color: $green;
				}
			}
		}
	}
}
</style>