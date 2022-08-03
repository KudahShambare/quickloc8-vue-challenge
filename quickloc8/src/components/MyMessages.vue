<template>
<h1>My Messages</h1>
<div id="messages" ref="messages">



</div>
</template>

<script>
import allMessages from "../messages.json";
//const json = require('json-loader!../colors.json'); invalid json file
 const colors=['#FF5722','#FFCCBC','#fe2a39']

export default{
    name:"MyMessages",
    mounted(){
    const listContainer=this.$refs.messages;
    //create messagwe
const createData=(val)=>{
    //div for single message
       let msgDiv=document.createElement("div");
       msgDiv.className="my-msg";
       console.log(msgDiv)
          //single div styling
     msgDiv.style.backgroundColor="lightgrey";
          msgDiv.style.display="flex";

             msgDiv.style.border="solid ";
                          msgDiv.style.marginTop="0.05%";

            
       //subsections for single message
       let msgImg=document.createElement("div");
       let msgContent=document.createElement("div")
       let msgDate=document.createElement("div")
       msgDiv.appendChild(msgImg)
              msgDiv.appendChild(msgContent)
       msgDiv.appendChild(msgDate)

    

       //single message icon
       let msgIcon=document.createElement("section");
       msgIcon.innerHTML=val.subject[0];
   
    //message icon style
       msgIcon.style.borderRadius="50%";
        msgIcon.style.height="auto";
        msgIcon.style.width="auto";
        msgIcon.style.marginTop="40%";
        msgIcon.style.paddingTop="30%";
        msgIcon.style.fontSize="x-large";
        msgIcon.style.fontWeight="bolder";
        msgIcon.style.backgroundColor=colors[Math.floor(Math.random()*colors.length)];
        msgIcon.style.width="10vw";

       msgImg.appendChild(msgIcon)
       //message content
       msgContent.style.width="70vw";
       //single message subject
       let msgTitle=document.createElement("h4");
        msgTitle.innerHTML=val.subject;
        msgContent.appendChild(msgTitle);
        //SINGLE MESSAGE FULL MESSAGE
        let fullMsg=document.createElement("p");
        fullMsg.innerHTML=val.message;
        msgContent.appendChild(fullMsg);
//single message date
let displayDate=document.createElement("h5");
displayDate.innerHTML=val.display;
msgDate.appendChild(displayDate)

            listContainer.appendChild(msgDiv);
}
allMessages.map((elem)=>{

createData(elem)
 

   
   
   
}
    )



    }
}
</script>

<style scoped>
#messages{
  
   min-height:50vh;
}
.my-msg{
    display:grid;
    grid-column:20% 60% 20%;
}

</style>