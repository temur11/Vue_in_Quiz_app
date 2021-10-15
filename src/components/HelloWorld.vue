<template>
  <div class="container">
    <div class="row">
      <div class="col-8 mt-5 offset-2 border">
        <div class="row  bg-secondary">
          <div class="col-12">
             <h1 class="text-center">Quiz App</h1>
          </div>
        </div>
     
       <div class="row" v-show=" ques">
       <div class="col-12 " v-for="(item, index) in questions.slice(a,b) " :key="index" @click="quec(item.id)"  >
         <h2 class="mt-2 text-center"> Savol </h2>
         <div v-if="item.see">
            <p class="text-center"> {{item.question}}</p>
           
          
           <li class="alert border list " v-for="(elements, index) in item.preposition"  :key="index" :class="select ? check(elements) : ''" @click="response(elements)">
            {{elements.props}}
           </li>
       </div>
        
        
       </div>
        
         <div class="col-12">
             <button class="btn btn-secondary float-left" @click="backresponse">Back</button>
           <button class="btn btn-success float-right" @click="nextResonse">Next</button>
         </div>
      
       </div>
      
       <div class="row" v-if="resSee">
         <div class="col-12">
           <h1 class="text-center">Answers: {{count}}/{{questions.length}}</h1>
           <h3 class="mt-2 text-center text-info">{{(count*100)/questions.length}}%</h3>
         </div>
       </div>
      
        <div class="row" v-if="resSee">
          <div class="col-12">
            <button class="btn btn-info" @click="restart">Restart</button>
          </div>
        </div>

      </div>
    </div>
   
  </div>
</template>

<script>
export default {
  data(){
    return{
      questions:[
        {
          id:1,
          question: "O'zbekistonni poytaxti qayer ?",
          preposition:[
            {props:'Samarqand' },
            {props:'Buxoro' },
            {props:'Toshkent', correct:true },
             {props:'Andijon'},
            
          ],
           see: true
          
        },
         {
            id:2,
          question: 'HTML da sarlavha teglari nechta ?',
          preposition:[
            {props:1},
            {props:3},
            {props:4, },
             {props:6, correct:true},
            
          ],
          see: true
         
        },
         {
            id:3,
          question: '3+5 = ?',
          preposition:[
            {props:2},
            {props:8, correct:true},
            {props:4, },
             {props:7 },
             
          ],
          see: true
        
        },
         {
            id:4,
          question: '4*5 = ?',
          preposition:[
            {props:12},
            {props:13, },
            {props:20, correct:true },
             {props:9 },
             
          ],
          see: true
         
        },
        
      ],
      a:0,
      b:1,
      select: false,
      count: 0,
     resSee:false,
     ques:true,
    
     

    }

  },
  methods:{
    restart(){
    //   this.a=0
    //   this.b=1,
    //   this.select= false,
    //   this.count= 0,
    //  this.resSee=false,
    //  this.ques=true
    Object.assign(this.$data, this.$options.data())
    },
     nextResonse(){
      if(this.questions.length == this.b){
        this.resSee=true
        this.ques= false
      }else{
          this.a++
          this.b++
          this.select=false
          

      }
   
    },
     check(e){
      
       if(e.correct){
         return 'correct'
       }else{
         return 'incorrect'
       }

     },
     response(e){
     
       this.select= true 
       if(e.correct){
         this.count++
       }
     },
     backresponse(){
       if(this.a>0){
         this.a--
         this.b--
        
       }

     },

   quec(e){

   setTimeout(() => {
      this.questions.forEach(item =>{
       if(item.id == e){
         item.see=false
       }
     })
     this.nextResonse()
   }, 1000);


    
   }

    //  quec(e){
    //      setTimeout(() => {
    //          this.questions.forEach((item) =>{
    //        if(item.id == e){
    //          item.see = false;
            
    //          this.nextResonse()
           
    //        }
    //   })
    //      }, 1000);
       
    
       
    //  }
  }

}
</script>

<style>

</style>