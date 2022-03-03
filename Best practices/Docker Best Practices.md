### Layer caching
This is used to reduce build times. Once a layer changes, all downstream layers have to be recreated as well. This process is similar to `.gitignore`. 
- Create a file `.dockerignore` in the same folder where dockerfile is.
- Incase of node app, supposing `node_modules` is added, this would ignore the directory 'node_modules' on build.
- To include the exceptions in the build, include `!` in front of the filename in the same file. For example, 
	```dockerignore
	# Excludes all markdown file from build
	*.md
	# includes README alone in the build 
	!README.md
	```

### Docker-compose example
```yml
version: "3.7"
services:
	app:
		image: node:12-alpine\
		command: sh -c "yarn install && yarn run dev"
		ports:
		- 3000:3000
		working_dir: /app
	volumes:
		- ./:/app
	environment:
		MYSQL_HOST: mysql
		MYSQL_USER: root
		MYSQL_PASSWORD: secret
		MYSQL_DB: todos
mysql:
	image: mysql:5.7
	volumes:
		- todo-mysql-data:/var/lib/mysql
	environment:
		MYSQL_ROOT_PASSWORD: secret
		MYSQL_DATABASE: todos
volumes:
	todo-mysql-data:
```


# Tags
#bestpractices