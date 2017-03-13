<template>
<div class="star" :class="starType">
  <p style="background-image: url('star24_half@2x.png')" ></p>
  <span v-for="itemClass in itemClasses" :class="itemClass" class="itemClass" track-by="$index"></span>
</div>
</template>

<script type="text/ecmascript-6">
  const  LENGTH = 5;
  export default{
    props:{
      size:{
        type: Number
      },
      score:{
        type: String
      },
    },
    created(){
      console.log(this.size+',,,'+this.score)
    },
    computed:{
      starType(){
        return 'star-'+this.size;
      },
      itemClasses(){
        let result=[];
        let  score=Math.floor(this.score*2)/2;
        let hasDecimal =score%1 !==0;
        let integer = Math.floor(score);
        for(let i =0 ;i<integer;i++){
          result.push('on');
        }
        if(hasDecimal){
          result.push('half')
        }
        while(result.length <LENGTH){
          result.push('off');
        }
        return result;
      }
    }
  }
</script>

<style>
  .star{
    font-size: 0;
  }
  .star .star-48 .star-item{
    width: 20px;
    height: 20px;
    margin-left: 22px;
    background-size:20px 20px ;
  }
  .star .star-48 .star-item :last-child{
    margin-right: 0;
  }
  .star .star-48 .star-item .on{
    background-image: url('star48_on@2x.png')
  }
  .star .star-36 .star-item .on{
    background-image: url('star48_on@2x.png')
  }
  .star .star-24 .star-item .on{
    background-image: url('star48_on@2x.png')
  }

  .star-item{
    display: inline-block;
    background-repeat: no-repeat;
  }

</style>
