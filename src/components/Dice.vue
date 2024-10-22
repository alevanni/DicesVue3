<script setup>
import { ref, reactive } from 'vue'



const count = reactive({
    1: 0,
    2: 0,
    3: 0,
    4: 0,
    5: 0,
    6: 0
})

const  throwEightTimes = () => {
    
    let thisRound = [];

    // we reset count to zero
    for (let i = 1; i < 7; i++) {
        count[i] = 0;
    }

    // we throw the dice
    for (let i = 0; i < 8; i++) {
        thisRound[i] = Math.floor(Math.random() * 6 + 1);
    }
    
    // we count
    thisRound.forEach( element => {
        count[element] += 1;
    });
    
    //console.log('result: ' + thisRound)
} 
</script>

<template>
    <div class="board">
        <h1>Throw the dice!</h1>
   
    <table>
        <thead>
            <tr>
                <th>Getal</th>
                <th>Aantal</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(result, key) in count" ><td>{{ key }}</td><td>{{ result }}</td></tr>
            
        </tbody>
    
    </table>
  
    <button @click="throwEightTimes">Gooi!</button>
    </div>
  </template>