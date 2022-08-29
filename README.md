

# redux-practice
# 1.State 
# 2.dispatch action
# 3.reducer
# 4.store 

const {createStore}=require("redux");

# defining action type as constrant
const INCREMENT="INCREMENT"
const DECREMENT="DECREMENT"
const ADD_USER="ADD_USER"

# 1. defineing state 
const initailCounterState={
    count:0
}

# 1. defineing Action 
# Action is a object . it has a type  and payload (for data transfer).

# increment Counter
const incrementConunter=()=>{
    return{
        type:INCREMENT
    }
}
const decrementConunter=()=>{
    return{
        type:DECREMENT
    }
}

# 3. create reducer for counter
# reducer is a function that will handle all logic based on action type 
const counterReducer=(state=initailCounterState,action)=>{
    switch(action.type){
        case INCREMENT:
            return{
                ...state,
                count:state.count+1,
            }
        case DECREMENT:
            return{
                ...state,
                count:state.count-1,
            }
        default:
            state;
    }

}


# 4.store - store has 
#          getState()->that will help to know all the condition of state,
#         dispatch()->that will to dispatch action,
#         subscribe()-> sbuscribe will help to subscibe from store to view .

# create Store
const store = createStore(counterReducer);

store.subscribe(()=>{
    console.log(store.getState());
})

# dispatch action
store.dispatch(incrementConunter())
store.dispatch(incrementConunter())
store.dispatch(incrementConunter())
store.dispatch(decrementConunter())
