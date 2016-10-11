<template>
    <div id="app" v-on:scroll="handleScroll">

        <section class="hero is-success margin-bottom-50">
            <div class="hero-body">
                <div class="container">
                    <h1 class="title">Grade Slider Thingy</h1>
                </div>
            </div>
        </section>

        <div class="container mainContainer">
            <grade-entry 
                :number_of_questions="number_of_questions" :out_of="out_of" :fixed_grade_entry="fixed_grade_entry" 
                v-on:gradeEntryChange="updateGradeEntry">        
            </grade-entry>
            <grade-table :number_of_questions="number_of_questions" :out_of="out_of"></grade-table>
        </div>
    </div>
</template>

<script>
import GradeEntry from './components/GradeEntry'
import GradeTable from './components/GradeTable'

export default {
  name:'APP',
  data() {
    return {
      number_of_questions:2,
      out_of:100,
      fixed_grade_entry: false,
    }
  },
  methods: {
    updateGradeEntry: function(data){
        this.number_of_questions = data.number_of_questions;
        this.out_of = data.out_of;
    },
    handleScroll: function(e) {
        var currentScrollPosition = e.srcElement.scrollTop;
        if(currentScrollPosition > 150) this.fixed_grade_entry = true;
        else this.fixed_grade_entry = false;
        // if (currentScrollPosition > this.scrollPosition) {
        //     console.log("Scrolling down");
        // }
        // this.scrollPosition = currentScrollPosition;
    }
  },
  components: {
    GradeEntry,
    GradeTable
  }
}
</script>

<style>
#app {
    overflow: scroll;
    height:100vh;
}
.margin-bottom-50 {
  margin-bottom:50px !important;
}

.mainContainer {
    padding:1em;
}

</style>
