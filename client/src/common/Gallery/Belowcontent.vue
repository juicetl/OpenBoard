<template>
  <div class="belowcontent">
    <div id = "below" ><p>点击选中的图类型：</p></div>
    
  </div>
</template>
  
  <script>
import { mapState } from "vuex";
export default {
  name: "belowcontent",
  components: {},
  data() {
    return {
      chartdata: {},
      mgeColor: false,
      // pwdColor: false
    };
  },
  computed: {
    ...mapState(["chartArray"]),
    charts:function(){
      return this.$store.getters.getchartArray;
    }
  },
  watch:{
    charts: function(data){
     let belowdiv = document.getElementById("below")
     belowdiv.innerHTML = ""
     var span = document.createElement("span")
     span.innerHTML = "点击选中的图形类型："+ data
     span.style.cssText = "font-size:20px;font-family:'Times New Roman'"
     belowdiv.appendChild(span)
    //  belowdiv.setAttribute("font-size","20px")
    //  belowdiv.innerHTML ="点击选中的图形类型："+ data

    }
  },
  mounted() {
    console.log(this.chartArray);
  },
  methods: {
  },
};
</script>
  
  
<style scoped>
.belowcontent{
  /* flex: 0.7 0 100px; */
  /* display: flex; */
  position:fixed;
  bottom:0;
  left:0;
  /* background-color: rgba(239,246,253); */
  background-color: rgb(242,242,242);
  width:100%;
  height:12%;
  /* flex-wrap: wrap; */
  /* overflow: auto; */

}
#blow{
  font-size:20px;
  font-family:'Times New Roman';
}
p{
  /* border:1px solid gray; */
  font-size:20px;
  font-family: 'Times New Roman';
}
</style>
  