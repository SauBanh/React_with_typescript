# React With Typescript
***
how to create app
With reactjs, command create a new project
```c
npx create-react-app reactapp
```

You will see it creates a folder called reactapp

***

As for react with ts, you use this command to create a new project

```c
npx create-react-app my-app --template typescript
 ```
## Working with components

- With component then you have to pass like that:

```c
import React from "react";

const Todos: React.FC<{ items: string[] }> = (props) => {
    return (
        <ul>
            {props.items.map((item) => (
                <li key={item}>{item}</li>
            ))}
        </ul>
    );
};

export default Todos;

```

- Should create a model and import into the component and create using that model
File todo.ts in models 
```c
class Todo {
    id: string;
    text: string;

    constructor(todoText: string) {
        this.text = todoText;
        this.id = new Date().toISOString();
    }
}

export default Todo;
```
In App.tsx
```c
import React from "react";
import Todos from "./components/Todos";
import Todo from "./models/todo";
import "./App.css";

function App() {
    const todos = [
        new Todo("Nguyễn Tuấn Anh đẹp trai"),
        new Todo("saubanh05062001@gmail.com"),
    ];
    return (
        <div>
            <Todos items={todos} />
        </div>
    );
}

export default App;
```
Component Todo.tsx
```c
import React from "react";
import Todo from "../models/todo";

const Todos: React.FC<{ items: Todo[] }> = (props) => {
    return (
        <ul>
            {props.items.map((item) => (
                <li key={item.id}>{item.text}</li>
            ))}
        </ul>
    );
};

export default Todos;
```

Component TodoItem.tsx

```c
const TodoItem: React.FC<{ text: string }> = (props) => {
    return <li>{props.text}</li>;
};

export default TodoItem;
```
