---
layout: post
title: react
categories: Living
tags: 
  - react
  - summery
img: http://or4d8nhvk.bkt.clouddn.com/18-4-1/89863742.jpg
---

# react学习demo

标签（空格分隔）： react

---
### 1.react状态的使用效果

![demo1](http://or4d8nhvk.bkt.clouddn.com/18-4-1/65066627.jpg)![demo2](http://or4d8nhvk.bkt.clouddn.com/18-4-1/53258689.jpg)

![demo3](http://or4d8nhvk.bkt.clouddn.com/18-4-1/66684360.jpg)
### 2.react代码

①index.js部分
```javascript
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>React-Template</title>
    <link rel="stylesheet" href="../css/main.css">
    <script src="https://cdn.bootcss.com/react/15.4.2/react.min.js"></script>
    <script src="https://cdn.bootcss.com/react/15.4.2/react-dom.min.js"></script>
    <script src="https://cdn.bootcss.com/babel-standalone/6.22.1/babel.min.js"></script>
  </head>
  <body>
    <div id="container"></div>
    <script type="text/babel">
    	
    	var Board = React.createClass({
    		
    		//返回一个初始化的数组对象
    		getInitialState:function(){
    			return({
    				comments:[]
    			});
    		},
    		
    		//更新修改后的信息
    		updateComment:function(newText,i){
    			//console.log(newText);
    			var arr = this.state.comments;
    			arr[i] = newText;
    			//更新数组
    			this.setState({comments:arr});
    		},
    		
    		//删除创建的一个组件
    		removeComment:function(i){
    			var arr = this.state.comments;
    			arr.splice(i,1);
    			this.setState({comments:arr});
    		},
    		
    		
    		
    		eachComment:function(text,i){
    				return(
    				  <Comment 
    				  updateCommentText={this.updateComment} key={i} index={i}
    				  deleteFromBoard={this.removeComment}
    				  >
    				  {text}
    				  </Comment>
    				);
    		},
    		
    		add:function(text){
    			var arr = this.state.comments;
    			arr.push(text);
    			this.setState({comments:arr});
    		},
    		
    		render:function(){
    			return(
    				<div>
    				<button onClick={this.add.bind(null,"Default text")} className="button-info create">Add New</button>
    				
    				   <div className="board">
    				   {
    				   	   this.state.comments.map(this.eachComment)
    				   }
    				   </div>
    				</div>
    			);
    		}
    	});
    	
    	var Comment = React.createClass({
    		  getInitialState:function(){
    		  	return ({editing:false});
    		  },
    		  
    		  edit:function(){
    		  	this.setState({editing:true});
    		  },
    		  
    		  remove:function(){
    		  	//alert("removing comment!");
    		  	this.props.deleteFromBoard(this.props.index);
    		  },
    		  
    		  save:function(){
    		  	var valu = this.refs.newText.value;
    		  	//console.log("拿到的值是："+valu);
    		  	this.props.updateCommentText(valu,this.props.index);
    		  	this.setState({editing:false});
    		  },
    		  
    		  renderNormal:function(){
    		  	return(
    		  		<div className="commentContainer">
    		  		  <div>{this.props.children}</div>
    		  		  <button onClick={this.edit}
    		  		  className="button-primary">Edit</button>
    		  		  
    		  		  <button onClick={this.remove} 
    		  		  className="button-danger">Remove</button>
    		  		</div>
    		  	)
    		  },
    		  
    		  renderForm:function(){
    		  	return(
    		  		<div className="commentContainer">
    		  		   <textarea ref="newText" defaultValue={this.props.children}></textarea>
    		  		   <button onClick={this.save} className="button-success">Save</button>
    		  		</div>
    		  	)
    		  },
    		  
    		  render:function(){
    		  	if(this.state.editing){
    		  		return this.renderForm();
    		  	}else{
    		  		return this.renderNormal();
    		  	}
    		  }
    		  
    	});
    	
    	ReactDOM.render(

    		<Board />,
    		document.getElementById("container")
    	);
    </script>
  </body>
</html>
```
②css部分（在下面的链接中）
[点击我看css样式代码](http://darknightduelist.xyz/project/two/main.css)
### 3.在线演示
[点我点我！](http://Darknightduelist.github.io/project/two/demo/eight/eight.html)