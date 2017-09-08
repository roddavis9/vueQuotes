<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote($event)"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote($event)"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">
          Click on a quote to delete it
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import QuoteGrid from './components/QuoteGrid.vue';
  import NewQuote from './components/NewQuote.vue';
  import Header from './components/Header.vue';

  export default {
    name: 'app',
    data () {
      return {
        quotes: [
            'Control the things that you can'
        ],
        maxQuotes: 4
      }
    },
    methods: {
        newQuote(quote) {
            if (quote) {
               if (this.quotes.length < this.maxQuotes) {
                this.quotes.push(quote);
               } else {
                  alert('delete some quotes before adding more');
               }
            }

        },
        deleteQuote(index) {
          this.quotes.splice(index, 1);
        }
    },
    components: {
        appQuoteGrid: QuoteGrid,
        appNewQuote: NewQuote,
        appHeader: Header
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
