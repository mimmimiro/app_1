<template>
  <Header />
    <main class="container">
	   <div v-for="recipe in recipes" :key="recipe.id">
        <div class="container__title">{{ recipe.strMeal}}</div>
          <div class="container__nathionality"><br> Nathionality:<br>{{ recipe.strArea }}</div>
          <div class="container__category"><br><br> Category: {{ recipe.strCategory}}</div>
          <div class="container__video"><a class="container__url" :href=url role="button">Video tutorial</a></div>
          <!-- <div class="container__source"><a :href=urlSource role="button"></a>link</div> -->
          <img class="container__image" :src=image>
          <div class="container__description">DESCRIPTION:<br>
	       {{ recipe.strInstructions}}</div>
	    <button class="container__button" @click="isRecipesVisible =!isRecipesVisible">Show ingredients</button>
	  
	   <section v-if="isRecipesVisible === true">
	     <ul class="container__list">
		    <li class="container__title-list">Ingredients:</li>
		    <li class="container__list">{{ recipe.strIngredient1 }},{{ recipe.strMeasure1}}</li>
		    <li class="container__list">{{ recipe.strIngredient2 }},{{ recipe.strMeasure2}}</li>
		    <li class="container__list">{{ recipe.strIngredient3 }},{{ recipe.strMeasure3}}</li>
		    <li class="container__list">{{ recipe.strIngredient4 }} {{ recipe.strMeasure4}}</li>
		    <li class="container__list">{{ recipe.strIngredient5 }} {{ recipe.strMeasure5}}</li>
		    <li class="container__list">{{ recipe.strIngredient6 }} {{ recipe.strMeasure6}}</li>
		    <li class="container__list">{{ recipe.strIngredient7 }} {{ recipe.strMeasure7}}</li>
		    <li class="container__list">{{ recipe.strIngredient8 }} {{ recipe.strMeasure8}}</li>
		    <li class="container__list">{{ recipe.strIngredient9 }} {{ recipe.strMeasure9}}</li>
		    <li class="container__list">{{ recipe.strIngredient10 }} {{ recipe.strMeasure10}}</li>
		    <li class="container__list">{{ recipe.strIngredient11 }} {{ recipe.strMeasure11}}</li>
		    <li class="container__list">{{ recipe.strIngredient12 }} {{ recipe.strMeasure12}}</li>
		    <li class="container__list">{{ recipe.strIngredient13 }} {{ recipe.strMeasure13}}</li>
		    <li class="container__list">{{ recipe.strIngredient14 }} {{ recipe.strMeasure14}}</li>
		    <li class="container__list">{{ recipe.strIngredient15 }} {{ recipe.strMeasure15}}</li>
		    <li class="container__list">{{ recipe.strIngredient16 }} {{ recipe.strMeasure16}}</li>
		    <li class="container__list">{{ recipe.strIngredient17 }} {{ recipe.strMeasure17}}</li>
		    <li class="container__list">{{ recipe.strIngredient18 }} {{ recipe.strMeasure18}}</li>
		    <li class="container__list">{{ recipe.strIngredient19 }} {{ recipe.strMeasure19}}</li>
		    <li class="container__list">{{ recipe.strIngredient20 }} {{ recipe.strMeasure20}}</li>
	     </ul>
		</section>
       <button class="container__button" @click="fetchRecipe">Get a new recipe</button>
		</div>
	 </main>
  <Footer />
</template>

<script>
  import Header from '../components/Header.vue';
  import Footer from '../components/Footer.vue';
    export default {
	  components: {
       Header,
	    Footer
	  },
	 data() {
		return {
			error:'',
			 recipes: [],
			 image: '',
			 url:'',
			 urlSource:'',
			 isRecipesVisible: false
		}
	},
	  computed: {
		 toggle() {
			if(this.isRecipesVisible) {
				return false
			}
			else return true
		}
	},
	  created() {
       this.fetchRecipe();
	},
	  
	  methods: {
		async fetchRecipe() {
      const url = 'https://www.themealdb.com/api/json/v1/1/random.php';
		const response = await fetch(url); 
		try {
			await this.handleResponse(response)
		} catch(error) {
			console.log(error)
			this.error = error;
		}
		},
		async handleResponse(response) {
			if(response.status >= 200 && response.status < 300)  {
				console.log('alt ok');
				const { meals }  = await response.json();
				this.recipes = meals;
				this.image = meals[0].strMealThumb
				this.url = meals[0].strYoutube
				this.urlSource = meals[0].strSource
				return true;
				} else {
					throw new Error ('noe gikk galt')
				}
		
	   },
   },
}
</script>

<style>
  .container__title {
	 text-align: center;
	 font-size: 2.2rem;
	 color: #4e5704;
	 margin: 1rem;
  }

  .container__category {
	 background: rgb(240, 181, 133);
	 box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
	 color: #414903;
	 width: 260px;
	 height: 250px;
	 margin: 60px;
	 border-radius: 180px;
	 text-align: center;
	 padding-top: 15px;
	 line-height: 2.2rem;
	 font-size: 1.7rem;
	 position: absolute;
	 top: 460px;
	 right: 95px;
  }

  .container__video {
	 background: rgb(240, 181, 133);
	 box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
	 color: #414903;
	 width: 180px;
	 height: 180px;
	 margin: 60px;
	 border-radius: 180px;
	 padding: 10px;
	 text-align: center;
	 line-height: 650%;
	 font-size: 1.5rem;
	 position: absolute;
	 top: 545px;
	 right: 320px;
  }

  .container__nathionality {
    background: rgb(240, 181, 133);
	 box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
	 color: #414903;
	 width: 300px;
	 height: 300px;
	 margin: 60px;
	 border-radius: 180px;
	 padding-top: 30px;
	 text-align: center;
	 line-height: 2.6rem;
	 font-size: 1.8rem;
	 position: absolute;
	 top: 250px;
	 right: 30px;
   }

  .container__url {
	 text-decoration: none;
	 color: #414903;
  }

  .container__image {
    margin: 15px 5px 10px 310px; 
	 width: 450px;
	 height: 450px;
  }

  .container__description {
	 font-family: cursive;
	 margin: 15px;
	 line-height: 1.6;
	 font-size: 1.1rem;
  }

   .container__title-list {
	  list-style: none;
	  line-height: 1.6rem;
	  margin-left: 15px;
	  font-size: 1.1rem;
	  font-weight: bold;
  }

   .container__list {
	  list-style: none;
	  line-height: 1.6rem;
	  margin-left: 15px;
	  font-size: 1rem;
   }

   .container__button{
      padding: 15px;
      border: 1px solid rgb(240, 181, 133);
      background-color: rgb(240, 181, 133);
      color: #414903;
      border-radius: 5px;
      width: 250px;
      margin:  15px;
      font-size: 1.6rem;
      box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
		font-family: cursive;
   }

   .container__button:hover,
   .container__button:active {
     background-color: #80a08a; 
     border-color: #80a08a; 
     color: #d4b506;
     box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
   }

   .container__video:hover,
   .container__video:active {
     background-color: #80a08a; 
     border-color: #80a08a; 
   }

   .container__url:active,
   .container__url:hover {
	   color: #c5a804;
   }

   @media screen and (max-width: 1024px) {
	  .container__title-list {
		  margin-left: 0px;
	   }

	  .container__image {
		  margin: 15px;
		  width: 690px;
		  height: 700px;
	   }

	  .container__description {
		  font-size: 0.8rem;
	   }

	   .container__list {
		  line-height: 2rem;
		  font-size: 0.8rem;
	   }
	  
	   .container__title-list {
		  margin-left: 15px;
		  margin-bottom: 15px;
	   }

	   .container__nathionality {
		  top: 300px;
		  right: 0px;
		  margin-left: 10px;
		  margin-right: 5px;
		  width: 280px;
		  height: 280px;
	   }

	  .container__category {
		  top: 530px;
        right: 5px;
		  margin-right: 5px;
	  }

	  .container__video {
		  top: 720px;
		  right: 20px;
   	}
}
</style>

