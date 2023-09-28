    <script>
      
    </script>
    
    <main class="component-2">
       <section class="form">
       <input  placeholder="Fullame"/>
       <input  placeholder="Phone Number">
       <input  placeholder="Email">
       <input  placeholder="Phone Number">
       <input  placeholder="Address">
       </section>

       <div class="btn-container">
        <button class="btn1">CANCEL</button>
        <button class="btn2">SAVE</button>
       </div>

    </main>
    
    <style>
        .component-2 {
        padding: 40px;
        width: 65%;
        height: 100%;
        margin-left: auto;
        align-items: center;
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
    
        @media (min-width: 640px) {
            main {
                max-width: none;
            }
        }
    </style>