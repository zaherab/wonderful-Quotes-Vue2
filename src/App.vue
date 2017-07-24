<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <app-new-quote @quoteAdded="newQuote"></app-new-quote>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <!-- row -->
        <div class="row">
            <!-- col-sm-12 text-center -->
            <div class="col-sm-12 text-center">
                <!-- alert alert-info -->
                <div class="alert alert-info">
                    Info : click on a Quote to delete it
                </div><!-- alert alert-info -->
            </div><!-- col-sm-12 text-center -->
        </div><!-- row -->
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue';
    import NewQuote from   './components/NewQuote.vue';
    import Header from  './components/Header.vue';

    export default {
        data(){
            return{
                quotes:[
                    'Just a quote to see something'
                ],
                maxQuotes: 10
            }
        },
        methods:{
          newQuote(quote){
          if(this.quotes.length >= this.maxQuotes){
              return alert('Delete Quotes to add new one');
          }
                this.quotes.push(quote)
          },
            deleteQuote(index){
              this.quotes.splice(index, 1);
            }
        },
        components:{
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
            appHeader: Header
        }
    }
</script>

<style>
</style>
