<template>
    <div>
        <h1 align="center" class="title">QuizApp</h1>
        <div class="qBox" v-bind:class="{ jo: joValasz, nemJo: rosszValasz}">
            <div class="q" align="center">
                <h2>{{kerdes[index].kerdes}}</h2>
            </div>
            <div class="aB">
                <button class="a" @click="check('v1',index)">A. {{kerdes[index].v1}}</button>
            </div>
            <div class="aB">
                <button class="a" @click="check('v2',index)">B. {{kerdes[index].v2}}</button>
            </div>
            <div class="aB">
                <button class="a" @click="check('v3',index)">C. {{kerdes[index].v3}}</button>
            </div>
            <div>
                <button class="button" @click="res()" v-bind:class="{ a1: eredmeny, a2: !eredmeny}">Következő</button>
            </div>
        </div>
        <h1 align="center" class="title" v-bind:class="{ a1: !eredmeny, a2: eredmeny}">Az eredményed: {{jo}}/10</h1>
    </div>
</template>
<script>
var kerdes=[
    {kerdes: "Melyik karakter tért vissza gonoszként a Tél katonájában?", v1: "Bucky Barnes", v2:  "Peggy Carter", v3: "Nick Fury", v: "v1"},
    {kerdes: "Melyik női Marvel hős kap először önálló filmet?", v1: "Scarlett boszorkány", v2:  "Fekete Özvegy", v3: "Marvel kapitány", v: "v3"},
    {kerdes: "Melyik filmben tűnt fel először a Fekete Özvegy?", v1: "A Bosszúállók", v2:  "Vasember 2.", v3: "A Hihetetlen Hulk", v: "v2"},
    {kerdes: "Melyik Galaxis őrzői szereplő cameózott már korábban?", v1: "Thanos", v2:  "Loki", v3: "a Gyüjtő", v: "v1"},
    {kerdes: "Melyik színész nem volt Hulk?", v1: "Matt Damon", v2:  "Mark Ruffalo", v3: "Edward Norton", v: "v1"},
    {kerdes: "Ebből az anyagból készült Amerika kapitány pajzsa és Vasember páncélja?", v1: "Mythrill", v2:  "Vibránium", v3: "Adamantium", v: "v2"},
    {kerdes: "Melyik filmben nem tűnik fel Tony Stark?", v1: "Thor", v2:  "A Bosszúállók", v3: "A Hihetetlen Hulk", v: "v1"},
    {kerdes: "Hány darab Végtelen kő létezik?", v1: "5", v2:  "6", v3: "7", v: "v2"},
    {kerdes: "Ronan milyen faj tagja?", v1: "Chituri", v2:  "Kree", v3: "Shi'tar", v: "v2"},
    {kerdes: "Ki volt az első Bosszúálló?", v1: "Steve Rogers", v2:  "Fekete Özvegy", v3: "Tony Stark", v: "v1"}
]
var index = 0;
var joValasz = false;
var rosszValasz = false;
var jo = 0;
var eredmeny = false;
export default {
    data(){
        return{
            kerdes: kerdes,
            index: index,
            joValasz: joValasz,
            rosszValasz: rosszValasz,
            jo: jo,
            eredmeny: eredmeny
        }
    },
    methods: {
        res(){
            if(this.kerdes.length-1<=this.index){
                this.eredmeny = true;
            }else{
            this.index+=1;
            this.joValasz = false;
            this.rosszValasz = false;
            }
        },
    check(mit, i){
        if(mit == this.kerdes[i].v){
            this.joValasz = true;
            this.jo++;
        }else{
            this.rosszValasz = true;
        }
    }
}
}
</script>
<style>
    body{
        background: #5cdb95;
        color: #edf5e1;
    }
    .qBox{
        background: #05386b;
        margin: auto;
        width: 60%;
        padding: 10px 10px 10px 10px;
        border-radius: 10px 10px 10px 10px;
    }
    .title{
        color: #edf5e1;
        text-shadow: 2px 2px black;
    }
    .a{
        background-color: #379683;
        border: none;
        color: white;
        padding: 15px 32px;
        text-align: center;
        text-decoration: none;
        display: block;
        font-size: 16px;
        margin: 4px 2px;
        cursor: pointer;
    }
    .button {
        display: inline-block;
        padding: 5px 5px;
        font-size: 18px;
        cursor: pointer;
        text-align: center;
        text-decoration: none;
        outline: none;
        color: #fff;
        background-color: #4CAF50;
        border: none;
        border-radius: 5px;
        box-shadow: 0 6px #999;
        float: right;
    }

    .button:hover {
        background-color: #3e8e41
    }

    .button:active {
        background-color: #3e8e41;
        box-shadow: 0 3px #666;
        transform: translateY(4px);
    }
    .jo{
        background-color: green;
    }
    .nemJo{
        background-color: red;
    }
    .a1{
        display: none;
    }
    .a2{
        display: inherit;
    }
</style>