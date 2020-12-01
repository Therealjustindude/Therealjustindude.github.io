---
layout: post
title:      "Losing Redux State on Refresh"
date:       2020-12-01 15:54:21 +0000
permalink:  losing_redux_state_on_refresh
---


 weBudget is my final project. It is an application that helps keep track of your monthly expenses and debts. It was created with a react front end and rails api. I use redux and thunk to make async calls to my back end, the data received from the fetch goes to my redux store and the updated user information is saved to localStorage. I didn’t know what localStorage was before this project. But, on page refresh I would loose my redux state. So I did some research and found out I would have to save my state there. This is also when I really understood component lifecycles. Putting a debugger everywhere helped too. 
 
	When I was losing global state on refresh and my tables would either show no data or the error ‘can not map property undefined,’ I was so confused. I didn’t do a fetch in component did mount of my app because a user needs to log in or sign up first. So, when app mounts it wouldn’t know which users information to get. Once logged in, the route changes to the users homepage and the user container component is rendered. Global state has the users information at this time. The user container takes that global state sets it in local state, passing it down to its children components as props.
	
	```
	<ExpensesTable currentUser={this.state.user.id} userExpenses={this.state.user.expenses} history={this.props.history} />
	<DebtTable currentUser={this.state.user.id} userDebts={this.state.user.debts} history={this.props.history}/>
	```
	
 The user container has two child components, 1) expenses table 2) debts table. They receive initial state from user container as props. 
	
```

state = {
	user_id: 0,
	expenses: this.props.userExpenses ? this.props.userExpenses : [],
	sortConfig: {
		key: 'date_due',
		direction: 'ascending'
	}
}
```


	
 Each table component is connected to the redux store so they can use dispatch and have access to the store when expenses or debts are added or updated. 

 The issue of losing global state was happening when you would refresh the page manually or when a refresh happens after a user submits an expense/debt. I tried putting a get fetch in component did mount of the user container. But because its async I couldn’t set local state in the user container using the redux store before the children components mount. So their props were empty. Causing the error can not map property of undefined.

 My fix, in each table, the component did mount lifecycle checks for a current user in local storage. If it finds one it means a user is signed in. Then it checks to see if any state was mapped to props from the redux store, if this is the case it means an instance has been created or updated and localStorage needs to update. If no state was mapped to props from the redux store, the component will grab the current user information from localStorage and set local state using that. 

 Let's say an expense was added, the expense table would see that state was mapped to props in the component did mount lifecycle. Then, the component removes current user information from local storage, sets local state with new user data from redux store and puts that updated user data in to localStorage. Now on refresh my components always have a local state. 
	

```
componentDidMount() {
		if (localStorage.getItem("currentUser")){
			if (this.props.user_expenses) { 
				const currentUser = JSON.parse(localStorage.currentUser)
				delete currentUser.expenses
				delete currentUser.debts
				localStorage.removeItem('currentUser')
				currentUser.expenses = this.props.user_expenses.expenses
				currentUser.debts = this.props.user_expenses.debts
				this.setState({
					...this.state,
					expenses: this.props.user_expenses.expenses ? this.props.user_expenses.expenses : currentUser.expenses,
					user_id: currentUser.id,
				})
				saveState(currentUser)
			} else {
				const persistedState = { user: loadState() }
				this.setState({
				expenses: persistedState.user.expenses,
				user_id: persistedState.user.id
				}) 
			}
		} 
	}
```
	

 I still have some features I want to add like, I want a user to be able to enter their pay days and I want to add a complete button that saves the completed months expenses to the db. But for now i’m satisfied with what I have. If you know of a better way to approach this problem, please let me know.
