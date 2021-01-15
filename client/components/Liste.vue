<template>
<div class="tout">

     <div class="form-box">
		<div class="header-text">
      <div class="titre">Pour vous !</div>
    <div>
    <button  class="button" @click="retrievetab()"><span>Afficher les produits disponibles</span></button>
    </div>
<div class="article-title">
    <article v-for="jouet in jouets" :key="jouet.id">
        
          <ul>
          <h3><li>{{ jouet.name }} - {{ jouet.description }}</li></h3>
          </ul>
        
    </article>
    </div>
    

  </div>
</template>

<script>
module.exports = {
props: {
    jouets: { type: Array, default: [] },
  },
  data (){
    return { 
      name:'',
      description:'',
      image:'',
      name2: ''
    }
  },

  methods: {

    researchname(){
      console.log('jesuisle1000emetest')
      this.$emit('research-name'),{
        name:this.name
      }
    },

    deletetoy(){
      console.log('DELETE LANCEE')
      this.$emit('delete-toy'),{
      name: this.name2
      }
    },

    async AjoutInvention(){
      await axios.post('/api/invente', {
        name: this.name,
        description: this.description,      })
    },

     retrievetab () {
      console.log('FONCTION LANCEE')
      this.$emit('retrieve-tab')
    }
  }
}

</script>

<style scoped>

.titre
{
 text-shadow:0 0 2px #FFD100,0 0 30px #FFD100,0px 0px 5px #FFD100, 0 0 150px #FFD100;color:#FFD100;
color:white;
}


.form-box {
	background-color: rgba(187, 187, 187, 0.096);
  margin: auto auto;
  margin-top: 75px;
  padding: 40px;
  margin-left: 410px;
	border-radius: 1px;
	box-shadow: 0 0 10px #000;
	position: absolute;
	top: 0;
	bottom: 0;
	left: 0;
	right: 0;
	width: 500px;
  height: 260px;
  font-family: poppins;
 
background-color:transparent;

color:white;
}
.form-box:before {
	width: 100%;
	height: 100%;
	background-size: cover;
	content: "";
	position: fixed;
	left: 0;
	right: 0;
	top: 0;
	bottom: 0;
	z-index: -1;
	display: block;
	filter: blur(2px);
}
.form-box .header-text {
	font-size: 32px;
	font-weight: 600;
	padding-bottom: 30px;
	text-align: center;
}
.form-box input {
	margin: 10px 0px;
	border: none;
	padding: 10px;
	border-radius: 1px;
	width: 100%;
	font-size: 18px;
  font-family: poppins;
  background: rgba(255, 255, 255, 0.185);
  opacity: 1;
  color: black;
}
.form-box input[type=checkbox] {
	display: none;
}
.form-box label {
	position: relative;
	margin-left: 5px;
	margin-right: 10px;
	top: 5px;
	display: inline-block;
	width: 20px;
	height: 20px;
	cursor: pointer;
}
.form-box label:before {
	content: "";
	display: inline-block;
	width: 20px;
	height: 20px;
	border-radius: 5px;
	position: absolute;
	left: 0;
	bottom: 1px;
	background-color: rgb(255, 255, 255);
}
.form-box input[type=checkbox]:checked+label:before {
	content: "\2713";
	font-size: 20px;
	color: #000;
	text-align: center;
	line-height: 20px;
}
.form-box span {
	font-size: 14px;
}
.form-box button {
	background-color: rgba(243, 244, 245, 0.473);
	color: #fff;
	border: none;
	border-radius: 1px;
	cursor: pointer;
	width: 100%;
	font-size: 18px;
	padding: 10px;
	margin: 20px 0px;
}

.button {
  display: inline-block;
  border-radius: 1px;
  background-color: transparent;
 
  color: #FFFFFF;
  text-align: center;
  font-size: 8px;
  padding: 10px;
  width: 80px;
  transition: all 0.5s;
  cursor: pointer;
  margin: 5px;
  
}

.button span {
  cursor: pointer;
  display: inline-block;
  position: relative;
  transition: 0.5s;
}


.button:hover span {
  padding-right: 10px;
  color:black;
  
}


input{
  margin-top: 100px;
}

/* Basic styles */
*,
*::before,
*::after {
  box-sizing: border-box;
}

:root{
    --bg-color: #D8D8D8;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
  width: 100vw;
  height: 100vh;
  color: #000;
  background-color: var(--bg-color);
  font-family: 'Maitree', serif;
}

h1{
    font-size: 3em;
    font-weight: normal;
}

/* title styles */
.home-title span{
  text-decoration: #000;
    position: absolute;
    overflow: hidden;
    display: inline-block;
 
}

.home-title span::after{
    content: '';
    position: absolute;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: white;
    animation: a-ltr-after 2s cubic-bezier(.77,0,.18,1) forwards;
    transform: translateX(-101%);
}

.home-title span::before{
    content: '';
    position: absolute;
    top: 0;
    right: 0;
    width: 100%;
    height: 100%;
    background: var(--bg-color);
    animation: a-ltr-before 2s cubic-bezier(.77,0,.18,1) forwards;
    transform: translateX(0);
}

.home-title span:nth-of-type(1)::before,
.home-title span:nth-of-type(1)::after{
    animation-delay: 1.2s;
}

.home-title span:nth-of-type(2)::before,
.home-title span:nth-of-type(2)::after{
    animation-delay: 1.8s;
}

@keyframes a-ltr-after{
    0% {transform: translateX(-100%)}
    100% {transform: translateX(101%)}
}

@keyframes a-ltr-before{
    0% {transform: translateX(0)}
    100% {transform: translateX(200%)}
}

html{
  scroll-behavior: smooth;
}
article {
  display: flex;
}

.article-img {
  flex: 1;
}

.article-img div {
  width: 100px;
  height: 100px;
  background-size: cover;
}

.article-content {
  flex: 3;
}


textarea {
  width: 100%;
}

h2{
  color: black;
}

h1 {
  position: absolute;
    top: 0px;
    margin-left: 470px;
    color: black;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}

.tout{
  position: absolute;
  margin-bottom: 200px;
}

h2{
  color: #000;
}

.article-title{
  font-size: 50%;
   color: #000;
   text-decoration: none;
   height:90px;
   width:250px;
overflow:hidden; 
overflow-y:scroll;}

</style>
