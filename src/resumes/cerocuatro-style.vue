<template>
<div class="resume" id="resume1">
  <div class="black-bar">
    <div class="row text-center">
      <span class="name">{&nbsp&nbsp{{person.name.first}}{{person.name.last}}&nbsp&nbsp}</span>
    </div>
    <div class="row text-center">
      <p class="position center">{{person.position}}</p>
    </div>
  </div>
  <div class="left half">
    <div style=margin-right:-10px; class="experience">
      <h3 class="uppercase">{{ lang.headings.experience }}</h3>
      <div class="experience-block" v-for="experience in person.experience" :key="experience.company">
        
        <span class="company"> {{experience.company}} </span>
        <span class="time-period"> {{experience.timeperiod}}</span>
        <span class="job-title"> {{experience.position}} </span>
        <!-- <span class="job-technologies">{{experience.technologies}}</span> -->
        <span v-if="experience.description" class="job-description"> {{experience.description}} </span>
        <span class="job-location"> {{experience.location}} </span>
      </div>
    </div>
    <div style=margin-right:-10px; class="contact">
      <h3 style=margin-right:-10px; class="uppercase">{{ lang.headings.contact }}</h3>
      <table style=margin-right:-15px;>
        <tr>
          <td><a :href="'mailto:'+person.contact.email" target="_blank">{{person.contact.email}}</a></td>
          <td><i class="fa fa-envelope" aria-hidden="true"></i></td>
        </tr>
        <tr style=margin-right:-10px; v-if="person.contact.phone">
          <td><a :href="'tel:'+person.contact.phone">{{person.contact.phone}}</a></td>
          <td><i class="fa fa-phone" aria-hidden="true"></i></td>
        </tr>
        <tr v-if="person.contact.street">
          <td>{{person.contact.street}} <br> {{person.contact.city}}</td>
          <td><i class="fa fa-home" aria-hidden="true"></i></td>
        </tr>
        <tr v-if="person.contact.website">
          <td><a :href="person.contact.website">{{person.contact.website}}</a></td>
          <td><i class="fa fa-globe" aria-hidden="true"></i></td>
        </tr>
        <tr v-if="person.contact.telegram">
          <td><a :href="'https://t.me/'+person.contact.telegram" target="_blank">t.me/{{person.contact.telegram}}</a></td>
          <td><i class="fa fa-telegram" aria-hidden="true"></i></td>
        </tr>
        <tr v-if="person.contact.skype">
          <td>{{person.contact.skype}}</td>
          <td><i class="fa fa-skype" aria-hidden="true"></i></td>
        </tr>
        <tr v-if="person.contact.github">
          <td><a :href="'https://github.com/'+person.contact.github" target="_blank">github.com/{{person.contact.github}}</a></td>
          <td><i class="fa fa-github" aria-hidden="true"></i></td>
        </tr>
        <tr v-if="person.contact.bitbucket">
          <td><a :href="'https://bitbucket.org/'+person.contact.bitbucket" target="_blank">bitbucket.org/{{person.contact.bitbucket}}</a></td>
          <td><i class="fa fa-bitbucket" aria-hidden="true"></i></td>
        </tr>
      </table>
    </div>
  </div>
  <div class="right half">
    <div class="education">
      <h3 style=margin-left:-10px; class="uppercase">{{ lang.headings.education }}</h3>
      <div style=margin-left:-10px; class="education-block" v-for="education in person.education" :key="education.degree">
        <span class="degree">{{education.degree}}</span>
        <span class="degree-description">{{education.description}}</span>
        <span class="degree-timeperiod">{{education.timeperiod}}</span>
        <span class="degree-latin">{{education.latin}}</span>
      </div>
    </div>
    <h3 style=margin-left:-10px;margin-top:-9px;>{{ lang.headings.skills }}</h3>
    <div class="skills">
      <div class="skill-block" v-for="skill in person.skills" :key="skill.name">
        <span class="skill">{{skill.name}}</span>
        <div class="skill-bar">
          <div :style="'width: '+skill.level+'%'" class="level"> </div>
        </div>
      </div>
    </div>
    <span class="skills-other"> {{person.knowledge}} </span>
  </div>
</div>
</template>

<script>
import Vue from 'vue';
import { getVueOptions } from './options';

let name = 'cerocuatro-style';
export default Vue.component(name, getVueOptions(name));
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
@mainColor: #303030;
#resume1 {
  &:after {
    content: "";
    position: absolute;
    z-index: 1;
    top: 224px;
    bottom: 24px;
    left: 50%;
    border-left: 2px solid @mainColor;
    transform: translate(-50%);
  }
  font-family:'Roboto' !important;
  font-size:18px;
  padding-bottom:50px;
  .uppercase {
    text-transform:uppercase;
  }
  a, a:focus, a:hover, a:visited {
    color:#616161;
  }
  h3 {
    margin-bottom:0;
    color: @mainColor;
  }
  span {
    display:inline-block;
  }
  .black-bar {
    height: 200px;
    background-color: @mainColor;
  }
  .row {
    width:100%;
  }
  .half {
    width:42%;
  }
  .half.left {
    float:left;
    text-align:right;
    padding-left:4%;
    padding-right:4%;
  }
  .half.right {
    float:right;
    text-align:left;
    padding-right:4%;
    padding-left:4%;
  }
  .center {
    margin-left:auto;
    margin-right:auto;
  }
  .text-center {
    text-align:center;
  }
  .name {
    // border:1px solid black;
    text-transform:lowercase;
    padding:68px 0px 0px 0px;
    // margin-top:80px;
    margin-bottom:5px;
    // font-family:'Open Sans', sans-serif;
    font-size:45px;
    font-weight:500;
    color: #FFFF;
    letter-spacing:2px;
  }
  .position {
    text-transform:uppercase;
    font-size:18px;
    color: #FFFF;
    margin-bottom:40px;
    letter-spacing:2px;
  }
  .image {
    width:100px;
    height:100px;
    margin-top:50px;
    margin-bottom:50px;
    .img {
      width:100%;
      height:100%;
      border-radius:50%;
      background-image:url('../../resume/id.jpg');
      background-repeat:none;
      background-position:center;
      background-size:cover;
    }
  }
  .contact {
    width:100%;
    table {
      text-align:right;
      float:right;
      margin-top:5px;
      color:#616161;
      i {
        padding:4px;
        color:#616161;
      }
      tr td:nth-child(2) {
        vertical-align:top;
      }
    }
  }
  .experience .experience-block span {
    width:100%;
    color:#616161;
  }
  .experience .experience-block span.company {
    font-weight:bold;
    padding-bottom:0px;
    padding-top: 15px;
    color:#424242;
  }
  .experience .experience-block span.time-period {
    font-style:italic;
  }
  .education-block span {
    color:#616161;

  }
  .education-block span.degree-timeperiod {
    width: 100%;
    font-style:italic;
  }
  .education-block span.degree {
    font-weight:bold;
    color:#424242;
    padding-top:15px;
  }
  .degree-latin {
    margin-bottom: -100px;
  }
  .skills-other {
    color:#616161;
    margin-bottom:10px;
  }
    .skills {
    margin-top:10px;
    margin-bottom:20px;
    margin-left:-10px;
    padding-right:-5px;
    .skill-block {
      padding-bottom:5px;
      display:inline-block;
      .skill {
        width:100px;
        color:#616161;
        float:left;
      }
      .skill-bar {
        float:right;
        background:#e0e0e0;
        overflow:hidden;
        height:8px;
        border-radius:3px;
        width:249px;
        margin-left: 40px;
        margin-top: -16.5px;
        .level {
          background:#757575;
          height:100%;
        }
      }
    }
  }
}
</style>
