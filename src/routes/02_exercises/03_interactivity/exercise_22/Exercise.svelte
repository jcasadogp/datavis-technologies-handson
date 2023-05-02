<script>
    let count = 0
    function clickButtom(event) {
      count = count +1;
    }

    function resetCount(event) {
      count = 0;
    }

  </script>
  
  
  <button class="sum" on:click={clickButtom}>Click</button>
  <button class="reset" on:click={resetCount}>Reset count</button>
  <p>You clicked the buttom {count} times</p>

  <style>
    button {
        background-color: green;
        border: none;
        color: white;
        padding: 15px 32px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
    }
    .reset{
        background-color: red;
    }
  </style>