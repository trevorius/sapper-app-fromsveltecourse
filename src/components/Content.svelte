<script>
  import Form from './Form.svelte';
  import ExpenseCard from './ExpenseCard.svelte';
  import { v4 as uuidv4 } from 'uuid';

  let cardsArray = [
    {
      id: uuidv4(),
      name: 'Shopping',
      amount: 300,
    },
    {
      id: uuidv4(),
      name: 'Games',
      amount: 150,
    },
    {
      id: uuidv4(),
      name: 'Books',
      amount: 250,
    },
    {
      id: uuidv4(),
      name: 'Udemi lessons',
      amount: 50,
    },
  ];

  $: total = cardsArray.reduce((acc, cur) => {
    return (acc += cur.amount);
  }, 0);

  const addCard = (event) => {
    let newExpense = {
      id: uuidv4(),
      name: event.detail.newExpense.name,
      amount: event.detail.newExpense.cost,
    };
    cardsArray = [...cardsArray, newExpense];
  };

  const removeThisCard = (event) => {
    cardsArray = cardsArray.filter((card) => event.detail.id !== card.id);
  };
</script>

<div class="container">
  <Form on:sendExpenseToParent={addCard} />
  <h2 class="my-4">Total Expenses : {total}</h2>
  {#each cardsArray as expense (expense.id)}
    <ExpenseCard
      name={expense.name}
      amount={expense.amount}
      id={expense.id}
      on:remove-this-card={removeThisCard}
    />
  {/each}
</div>
