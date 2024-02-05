## Frontend Frameworks ?

    Why these frameworks exist.
    what problems do they solve. 
    why we use React/Vue/etc.


DOM Manipulation

    DOM manipulation is very hard to write as a developer.
    Which means making dynamic websites, with the premitives that DOM provides
    you is very hard.
    So that is the reason React is introduced.

    - Primitives provided by DOM :
        document.createElement
        document.appendChild
        element.setAttribute
        element.children
        
Todo app


        <html>
            <script>
                let globalId=1;
                function markasDone(id){
                    const parent =document.getElementById(id);
                    console.log(parent);
                    parent.children[2].innerHTML="Done!"
                }
                function createChild(title, description, id){
                    const child = document.createElement("div");
                    const titlediv = document.createElement("div");
                    titlediv.innerHTML=title;
                    const descrioptiondiv = document.createElement("div");
                    descrioptiondiv.innerHTML=description;
                    const buttondiv = document.createElement("button");
                    buttondiv.innerHTML= `Mark as Done!`;
                    buttondiv.setAttribute("onClick", `markasDone(${id})`);
                    child.appendChild(titlediv);
                    child.appendChild(descrioptiondiv);
                    child.appendChild(buttondiv);
                    child.setAttribute("id", id);
                    return child;
                }
                function addTodo(){
                    const title = document.getElementById("title").value;
                    const description = document.getElementById("description").value;
                    document.getElementById("container").appendChild(createChild(title, description, globalId++));
                }
            </script>
            <body>
                <input id="title" type="text" placeholder="title"><br></br>
                <input id="description" type="text" placeholder="description"><br></br>
                <button onclick="addTodo()">Add Todo</button>
                <div id="container"></div>
            </body>
        </html>

We tried to create a Todo app using DOM manipulation

    Problem with this approach is that, it is hard ti add and remove elements.
    also, no central state.

What is State?
    generally refers to the current condition or status of a web page or a specific element on the page.

    In web development, managing state is crucial for creating dynamic and interactive user interfaces. Stateful applications often involve updating the DOM in response to user actions or changes in data. JavaScript is commonly used to manipulate the DOM and manage the state of a web page.

    For example, consider a to-do list application. The state of each to-do item might include information such as the task name, completion status, and any additional details. When a user interacts with the application, like adding a new task or marking a task as completed, the state of the DOM elements representing the to-do items needs to be updated to reflect these changes.


So if we can write a function, that takse this state as an input and creates the output we want, that is 
much more powerful than the above todo code we had written.