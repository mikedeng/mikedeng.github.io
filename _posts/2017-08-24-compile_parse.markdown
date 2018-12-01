---
layout: post
title:  "js模板解析"
date:   2017-08-24 22:30:39

categories: frontend
---


+ 问题： js如何解析模板

+ 解决办法：

	```javascript

		var template = `
			<ul>
				<% for (var i = data.suppliers.length - 1; i >= 0; i--) { %>
					<li><%= data.suppliers[i] %></li>
				<% } %>
			</ul>
		`;

		//目标

		echo('<ul>');
		for (var i = data.suppliers.length - 1; i >= 0; i--) {
			echo('<li>');
			echo(data.suppliers[i]);
			echo('</li>');
		}
		echo('</ul>');

		function compile(template) {
			var regExpr = /<%=(.*?)%>/g;
			var reg 		= /<%([\s\S]+?)%>/g;
			template = template.replace(regExpr, '`) \n echo($1) \n echo(`').replace(reg, '`) \n $1 echo(\n`');
			template = 'echo(`' + template + '`)';

			let scripts = `(function(data){
				let output = "";
				function echo(html){
					output += html;
				}

				${template}
				return output;
			})`;

			return scripts;
		};

		var parse = eval(compile(template));
		console.log(parse({suppliers: [1111,2,3,3,3,3,4,4,4,4,44444]}));

	```