<script>
//import 
import Icon from '@iconify/svelte';
  import { each } from 'svelte/internal';

// varaibiles
let activeComponent ;
let contacts=[]
let selectedContact={}
let validationNameError;

//contact varaibles
let fullname;
let dateofbirth;
let email;
let phonenumber;
let address

//functions
const showAddContactModal = function (){
    fullname=email=address=phonenumber=dateofbirth=''
    selectedContact={}
    activeComponent="component-2"
}
const closeAddContactModal = function (){
    fullname=email=address=phonenumber=dateofbirth=''
    activeComponent=""
}

const saveContact = function (){
    //for updating  the contact list
      
    if( Object.keys(selectedContact).length > 0){
      const data = contacts.filter((contact)=>contact!==selectedContact)
      const nameIsUsed = data.some((item)=>item.fullname===fullname)  
      if(nameIsUsed){
        validationNameError='you already have a contact saved with this name'
        return
      }
      contacts=[...data,{fullname,dateofbirth,email,phonenumber,address}]
      activeComponent=''
      return
  
    }
    const nameIsUsed = contacts.some((item)=>item.fullname===fullname)  
      if(nameIsUsed){
        validationNameError='you already have a contact saved with this name'
        return
      }   
    contacts=[...contacts,{fullname,dateofbirth,email,phonenumber,address}]
    fullname=email=address=phonenumber=dateofbirth=''
    console.log(contacts)
    activeComponent=""
}

const showEditContactModal = function(){
    fullname=selectedContact.fullname
    email=selectedContact.email
    address=selectedContact.address
    dateofbirth=selectedContact.dateofbirth
    phonenumber=selectedContact.phonenumber
    activeComponent='component-2'
}

const showComponent3 = function(data){
    selectedContact=data
    activeComponent="component-3"
}

const deleteContact = function(data){
    const newData = contacts.filter((contact)=>contact!==data)
    contacts=newData
    activeComponent=''
}


</script>

<main class="container">

<main class="component-1">
   <div class="main-header">
    <div class="sub-header">
    <h1>CONTAXTS</h1>
    <p class="tm">TM</p>
   </div> 

   <div on:click={showAddContactModal}>
   <Icon icon="typcn:plus" color="white"  width="30" height="30" style="font-weight:bold; cursor:pointer;   "/>
   </div>

   </div>  
   
   <div>
    {#each contacts as contact,index (contact)}
    <div on:click={()=>showComponent3(contact)} key={index} style="color: aliceblue; cursor:pointer">{contact.fullname}</div>
    {/each}
   </div>



</main>

<main
 class="component-2"
 style="{activeComponent==='component-2'?'display:block;' : 'display:none;'}"
>
    <section class="form">
    <input bind:value={fullname} type="text" placeholder="Fullame"/>
    <div
    style="{validationNameError?'display:block;' : 'display:none;'}"
    ><Icon icon="icon-park-outline:caution" color="red"  width="30" height="30"/>{validationNameError}</div>
    <input bind:value={phonenumber} type="text" placeholder="Phone Number">
    <input bind:value={email} type="text" placeholder="Email">
    <input bind:value={dateofbirth} type="date" placeholder="Date of birth">
    <input bind:value={address} type="text" placeholder="Address">
    </section>

    <div class="btn-container">
     <button class="btn1" on:click={closeAddContactModal}>CANCEL</button>
     <button class="btn2" on:click={saveContact}>SAVE</button>
    </div>

 </main>

 <main
  class="component-3"
  style="{activeComponent==='component-3'?'display:block;' : 'display:none;'}"
 >
 
 <div
 class="edit-buttons-container"
 >
 <button on:click={showEditContactModal} style="all: unset; margin-right:20px">
 <Icon icon="noto:fountain-pen" color="white"  width="30" height="30" style="font-weight:bold; margin-right:20px; cursor:pointer;   "/>
 <button>

 <button style="all: unset;" on:click={()=>deleteContact(selectedContact)}>
 <Icon icon="emojione-v1:scissors"   width="30" height="30" style=" cursor:pointer;   "/>
 </button> 

</div>

 <h1>NAME</h1>
 <div>{selectedContact.fullname?selectedContact.fullname:''}</div>

 <h1>EMAIL</h1>
 <div>{selectedContact.email?selectedContact.email:''}</div>

 <h1>PHONE NUMBER</h1>
 <div>{selectedContact.phonenumber?selectedContact.phonenumber:''}</div>

 <h1>BIRTHDAY</h1>
 <div>{selectedContact.dateofbirth?selectedContact.dateofbirth:''}</div>

 <h1>ADDRESS</h1>
 <div>{selectedContact.address?selectedContact.address:''}</div>
 </main>

</main>

<style>
    .container {
        display: flex;
        flex-direction: row;
        width: 100%;
        height: 100%;
    }
	.component-1 {
    background-color: #648570;
    width: 35%;
    height: 100vh;
    padding: 20px;
    /* margin-left: auto;/take component to the left */
	}

    .tm{
        margin-top: 6px;
    }

    .main-header{
        display: flex;
        align-items: center;
        color: white;
        justify-content: space-between;
    }

    .sub-header{
        display: flex;
        align-items: center;
        color: white;
    }


    @media (min-width: 768px) and (max-width: 1023px) {
    h1 {
        font-size: 28px;
        margin-bottom: 15px;
    }

    p {
        font-size: 18px;
    }
}

.component-2 {
        padding: 40px;
        width: 100%;
        height: 100%;
        margin-left: auto;
        flex-direction: column;
        }

        .btn1{
          border-radius: 6px;
          padding:5px 20px;
          border:1px solid #648570;  
          color: #648570;

        }

        .btn2{
          border-radius: 12px;
          padding:5px 20px; 
          background-color: #648570;
          color: white;  
          margin-left: 20px;
        }

        input {
         margin-top: 30px;
         width: 100%;
         height: 40px;
         padding: 10px;
         border: 2px solid #ccc; /* Default border color */
         border-radius: 5px; /* Border radius */
         border-bottom-color: #648570; /* Upper border color */
         outline: none; /* Remove default outline on focus */
         cursor: pointer;
}

            /* Add hover and focus styles for better user interaction */
            input:hover,
            input:focus {
                border-color: #648570; /* Border color on hover and focus */
            }

        .form{
            display: flex;
            flex-direction: column;      
        }

        .btn-container{
            display: flex; /* Added this to make main a flex container */
            justify-content: center; /* Centers horizontally */
            margin-top: 30px;
        }
        

        .component-3 {
        padding: 40px;
        width: 65%;
        height: 100%;
        margin-left: auto;
        flex-direction: column;

        }
        .edit-buttons-container{
            display: flex;
            flex-direction: row;
        }


        @media (min-width: 640px) {
            main {
                max-width: none;
            }
        }
        /* Media query for small screens (e.g., mobile phones) */
        @media (max-width: 767px) {
            h1 {
                font-size: 16px;
                margin-bottom: 5px;
            }

            p {
                font-size: 8px;
            }

            main {
                padding: 10px;
            }
        }
</style>