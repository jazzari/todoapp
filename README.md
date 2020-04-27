
Routes (/config/routes.rb)
Restful routes
- resources :todos 


In the Model (Class Todo) (/models/todo.rb)
Validation of attributes
- validates :name, presence: true
- validates :description, presence: true


In the Controller (todos_controller) (/controllers/todos_controller.rb)
For a New Action:
- Initiate a todo instance variable (avaible in the controller and in the views)
-@todo = Todo.new

For a Create Action:
CREATE - uses the submited info from the form and puts it in an instance variable
- @todo = Todo.new(todo_params) # uses strong parameters (todo_params)
save the object in the database:
- @todo.save
- flash notification
redirect to show the new saved object: (if it's saved)
- redirect_to todo_path(@todo) # (@todo) gives the :id
redirect to new action (if an error occurs and it's not saved)

For a Show Action:
Find the id of the object and assign the object to a instance variable
- @todo = Todo.find(params[:id])

For an Edit Action:
Using a form to edit an existing object
Then submits to update -> hits the database with patch or gives an error
- first find the existing object to be edited
- similar to create action, but using update
- if an error occur then redirect to edit action


STRONG PARAMETERS:
In the "private" section define a method colled "todo_params" that require
the top key (:todo), and permit only values for :name and :description
- params.require(:todo).permit(:name, :description)



In the Views (/views/todos)
Corresponding actions to resources:

 NEW - form to create a new todo
checks for possible errors for an attempt to save an object  
submits to create - hits the database o gives an error

SHOW - shows a particular object saved in the database
Display the object using the instance variable 


FLASH (show "temporary" messages to the user)
FLASH is a hash, and I can put messages in a flash (in the controller's action)
Then I can display that messages (in the corresponding view or in the  layout)

