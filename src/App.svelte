<script>
  import Comp1 from './lib/Comp1.svelte'
  import Comp2 from './lib/Comp2.svelte'
  import Comp3 from './lib/Comp3.svelte'
  import TopMenu from './lib/TopMenu.svelte'
  
  //Массив объектов, содержащий ссылки на 3 компонента
  const options = [
      {  component: Comp1 },
      {  component: Comp2 },
      {  component: Comp3 },
    ];
  
    let selected = options[0]; //компонент по умолчанию
  
    function SelectComp(idcomp){
      //Функция вызывается из верхнего меню и определяет
      //выбранный пользователем компонент
       selected = options[idcomp]
      
    }
  
    
  
    let current_message; 
  
    function SendMessage(mess){
      //функция вызывается из компонентов Comp1, Comp2 и Comp3
      //Каждый из них формирует свое сообщение, к-е передается
      //через аргумент mess  и определяет переменную current_message.
      //Current_message передается в компонент Detector через prop messagefrom
       current_message = mess
       clicked = true
       setTimeout(() => {
        clicked = false
       }, 200);
  
    }
  
  let clicked = false;
  </script>
  
  <main>
  <!-- The Holy Grail page structure -->
  <div class="holy-grail">
    <header>
      <!-- Header content -->
      <nav> 
        <TopMenu selectcomp = {SelectComp}/> 
      </nav>
    </header>
    <div class="container">
      <div class="main-content">
        <!-- Динамические компоненты -->
        <svelte:component 
           this={selected.component} 
           app_function={SendMessage} />
  
      </div>
    </div>
    <footer>
      <!-- Footer content -->
      <p>&copy; 2024 Holy Grail Page</p>
    </footer>
  </div>
  
  </main>
  
  <style>
  /* Global styles */
  :root {
    font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
    line-height: 1.5;
    font-weight: 400;
  }
  
  
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  
  .holy-grail {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
  
  header {
    background-color: #333;
    color: #fff;
    padding: 1em;
    text-align: center;
  }
  
  .container {
    display: flex;
    flex-wrap: wrap;
    padding: 20px;
    flex: 1;
  }
  
  .main-content {
    flex: 3;
    padding: 20px;
  }
  
  footer {
    background-color: #333;
    color: #fff;
    padding: 1em;
    text-align: center;
    height: 50px;
    margin-top: auto;
  }
  
  /* Responsive styles */
  @media (max-width: 1200px) {
  }
  
  @media (max-width: 992px) {
  }
  
  @media (max-width: 768px) {
    .container {
      flex-direction: column;
    }
    .main-content {
      flex: 1;
    }
  }
  </style>