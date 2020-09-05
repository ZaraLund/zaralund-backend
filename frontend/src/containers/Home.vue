

<template>
<div>
        <header id="top" class="header">
            <div class="intro-message">
                <h1>Hi,</h1>
                <h2>I'm Zara P Lundgren</h2>
                <h3>I'm a Full-Stack Developer living in Timrå, Sweden.</h3>
            </div>
        </header>
<div class="contentbox">
   <div class="uk-card uk-card-default uk-grid-collapse uk-child-width-1-2@s uk-margin" uk-grid >
      <div class="uk-card-media-left uk-cover-container">
        <img src="../assets/me.jpg" alt="" uk-cover style=" width:470px; height:400px;">
        <canvas width="470" height="400"></canvas>
      </div>
    <div>
        <div class ="uk-card-header">
          <h3>Zara Lundgren</h3>
        </div>
        <div class="uk-card-body">
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna 
            aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis
            aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat 
            cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</p>
        </div>
         <div class="uk-card-footer" style="margin: 20px;">
               <a href="#" class="uk-button uk-button-text">Read more</a>
         </div>
    </div>
  </div>

  <svg version="1.1" id="line_2" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" width="1200px" height="5px" xml:space="preserve">
  <path class="path2" fill="#01a09e" stroke-width="3" stroke="#f0f0f0" d="M0 0 l1120 0"/>
</svg>
<h3 style="text-align:center; margin: 10px;">My Skills</h3>


<div class="box">
  <div class="skillbox" id="card-box" v-for="(skills, index) in skills" :key="index" >
    <div id="card3">
      <div class="front face">
        <img :src="api_url + skills.image.url" alt="" height="100" />
      </div>
      <div class="back face">
        <h1>{{skills.title}}</h1>
        <p class="artist">{{skills.description}}</p>
        <p class="date">2015</p>
      </div>
    </div>
  </div>
</div>
</div>

     <header id="top" class="header">
            <div class="intro-message">
                <h1>Hi,</h1>
                <h2>I'm Zara P Lundgren</h2>
                <h3>I'm a Full-Stack Developer living in Timrå, Sweden.</h3>
            </div>
        </header>

        <div>
 <div class="uk-section">
      <div class="uk-container uk-container-large">
        <ArticlesList :articles="articles"></ArticlesList>
      </div>
  </div>
</div>

</div>

</template>




<script>
import ArticlesList from "../components/ArticlesList.vue";
import gql from "graphql-tag";


export default {
  
  components: {
    ArticlesList
  },
  data: function() {
    return {
      articles: [],
      skills: [],
      api_url: process.env.VUE_APP_STRAPI_API_URL
      };
  },
  apollo: {
    articles: gql`
      query Articles {
        
        articles {
          id
          title
          content
          image {
            url
          }
          category {
            name
          }
        }
      }`,
    skills: gql`
      query Skills {
        skills {
          id
          title
          description
          image {
            url
          }
        }
      }`
  }, 
};
</script>
