# AngularJS Notes

*** 

## Key Players in AngularJS

```
     ________
    | Module |
    ----------
     ________
    | Router |
    ----------    
 ___________  ______________
|    UI    | | Logic / Data |
|----------| |--------------|
|   View   |-|  Controller  |
|----------| | -------------|
|Directives| |   Factory    |
|----------| |--------------|
|  Filter  | |   Service    |
------------ ----------------
```

### Module
Container for your application. (ex. Directives, Factory, COntrollers)

### Route
- Router: Get to know which view will be loaded, a path of URL in browser
- Reference a controller and view
- Can include route parameters: 
- /customer/:customerId

### UI
#### Views
- Render the user interfaces:
- Contain HTML, CSS
- Bind the data provided by a controller via a $scope object
- Use directive to enhacne HTML and render data

#### Directives
enhance HTML binding the data into the View

#### Filter
Provide some data filtering functionality(ex uppercase data)

### Logic/Data
#### Contorller: 
- Brain for our view. 
- Retrieve data from a factory/service and store it. 
- Handle events triggered by the view.
- Know how to handle custom logic.
- Rely on the $scope object to interact with the view.
- Once contorller gets the data, we want to let those data into the View by using $Scope.

#### $Scope(ViewModel)
- Glues our UI side with Logic/data Side.
- A data for a View, and scope is the Model of data in the View.

#### Factory & Service: 
- Used to make RESTful calls 
- Share data between controllers
- Handle custom logic 
- (ARE Singletons) 
- All things are sharable and resuable, provide great way to encapsulate resuable functionality.

***
## View / Directives / Filter 


## Data Binding

"Two way" data binging can lead to significant reductions in code.

1. Property is bound to the textbox(ex)
2. User modify Data
3. Property value is automatically updated!

## Directives and Expression

Teach HTML new tricks!
- Dom manipulation(ng-hide/ng-show/ng-repeat/ng-view)
- Data Binding(ng-build/ng-init/ng-model)
- Controller/Module(ng-app/ng-controller)
- View Loading(ng-click/ng-keypress)
- CSS
- Event Handling

```js
<html ng-app>
<head>
    <title>Iterating Over Data</title>
</head>
<body ng-init="people=[{join:'2002-12-12', orderTotal: '2300', name:'Kevin', city:'Dallas'},{join:'2002-03-12', orderTotal: '2022', name:'Peter', city:'Chandler'},{join:'2002-12-12', orderTotal: '2000', name:'John', city:'Chandler'} ]">
    <h3>Iterating through data with ng-repeat</h3>
       Filter: <input type = "text" ng-model = "customerFilter.name" />
        <br /><br />
        <table>
            <tr>
                <th ng-click = "sortBy = 'name'; reverse = !reverse">Name</th>
                <th ng-click = "sortBy = 'city'; reverse = !reverse">City</th>
                <th ng-click = "sortBy = 'orderTotal'; reverse = !reverse">Order Total</th>
                <th ng-click = "sortBy = 'join'; reverse = !reverse">Joined</th>
            </tr>
            <tr ng-repeat="person in people | filter:customerFilter | orderBy: sortBy : reverse" >
                <td>{{person.name}}</td>
                <td>{{person.city}}</td>
                <td>{{person.orderTotal | currency }}</td>
                <td>{{person.join | date }}</td>
            </tr>
        </table>
    <script src="angular.js"></script>
</body>
```

***

## Controllers

