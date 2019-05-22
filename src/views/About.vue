<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>

<script>
console.log("test")

var brain = require('brain.js');




export default {

  name: "about",
  created: function(){
    //https://github.com/BrainJS/brain.js#node
    const net = new brain.NeuralNetwork();

net.train([{input: { r: 0.03, g: 0.7, b: 0.5 }, output: { black: 1 }},
           {input: { r: 0.16, g: 0.09, b: 0.2 }, output: { white: 1 }},
           {input: { r: 0.6, g: 0.78, b: 1.0 }, output: { white: 1 }},
           {input: { r: 0.7, g: 0.88, b: 1.0 }, output: { white: 1 }},
           {input: { r: 0.6, g: 0.9, b: 1.0 }, output: { white: 1 }},
           {input: { r: 0.77, g: 0.88, b: 1.0 }, output: { white: 1 }}]);

const output = net.run({ r: 0.03, g: 0.6, b: 0.4 });  // { white: 0.99, black: 0.002 }
  console.log(output);
  console.log(net.toJSON());



const fruitnet = new brain.NeuralNetwork();

fruitnet.train([{input: { r: 0, g: 1, b: 0 }, output: { green: 1 }},
           {input: { r: 1, g: 1, b: 0 }, output: { yellow: 1 }},
           {input: { r: 1, g: 0, b: 0 }, output: { red: 1 }},
           ]);

const fruitoutput = fruitnet.run({ r: 1, g: 1, b: 0 });   // 88% sure it is yellow
  console.log(fruitoutput);
  console.log(fruitnet.toJSON());

  /*

  green: r: 0, g: 1, b: 0
  yellow: r: 1, g: 1, b: 0
  red: r: 1, g: 0, b: 0
  
 



    const X = [['Green', 3], ['Yellow', 3], ['Red', 1], ['Red', 1], ['Yellow', 3]];
    const y = ['Apple', 'Apple', 'Grape', 'Grape', 'Lemon'];
    decision.fit({ X, y });
    decision.printTree(); // try it out yourself! =)

    decision.predict({ X: [['Green', 3]] }); // [ 'Apple' ]
  */


  }

}
</script>

<style>

</style>
