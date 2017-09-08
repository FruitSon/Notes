
##Udenmy - NG for beginners
```
Difference of NG1 & NG2: http://www.cnblogs.com/1wen/p/5564368.html
```

##basics
extends HTML, for dynamic website
customize tag in html
separate view with web logic
2-way data binding
- 2 way data binding allows us to bind a variable in both directions which will cause our view to be instantly updated when modifying our model.
dependency injection (hold the element)

##MVC
Module：store data , manage logic （data的中转站
View：interface user can see
Controller：accept input and converts it to commands to update M or V
￼
	
##Controller
1.create Module
2.create Controller (belongs to module, chain rule)
angular.module(“name-of-module”,[dependencies])
.controller("name-of-controller-of-this-module”,[“params-to-be-passed-to-function”,function(params){
//传进去的参数要对应呀
}]);
3.attach controller to view 
-use directives to link controller to DOM-E, the controller will then control everything inside the DOM-E
-directives are markers on a DOM 
-attach mutliple controllers

##Expressions
{{expressions}}
1.able to use data stored in module directly

##2way Data Binding
1.data binding: view data is bind to module data, so no need to reach DOM to get data
2.enable view to affect model: “ng-model”

##Directives
1.customized HTML tag, extend functionality of HTML
-“ attach a specified behavior to that DOM element (e.g. via event listeners), or even to transform the DOM element and its children.”
.directive(“name-of-directive”,function(){
	//return an object
	return{
		restrict:"E",   //applicable situation
		template:"<div>How are you</div>”,
		replace: true	//‘E’时生效，dom里没有<name></name>
	}
});
2.Restricted to ‘A’ & ‘E’ by default. 
-use restrict option： 
-‘A’  attribute name <div people="Harry"> </div>
-‘E’ - element name <people>    </people>
%-‘C’ - class name <div class="people:Harry"> </div>
%-‘M’ - comment
3.auto transform name for usage: ng用驼峰式命名, split by capital letter, e.g. “welcomeMsg” ->“welcome-msg”
-HTML对大小写不敏感，而JavaScript对大小写敏感
4.apply pre-fix to avoid conflict

##Service
##Scopes

##Filters

##Routing- Setup

##Routing- Implementation
