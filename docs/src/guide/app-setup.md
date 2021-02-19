# App Local Environment Setup

## Mac OS

Instructions are using the following tools:

-   [Microsoft VS Code](https://code.visualstudio.com/download)
-   [Docker Desktop](https://www.docker.com/products/docker-desktop)

For Microsoft VS Code, it is suggested to use the following extensions:

-   [Docker by Microsoft](https://marketplace.visualstudio.com/items?itemName=formulahendry.docker-extension-pack)
-   [Live Share by Microsoft](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare-pack)

### Step 1 - Clone development environment repository from Github

1. **Clone** the repository using the following command:

```zsh
% git clone https://github.com/WhatsUp247/wu247docker.git
```

2. **Copy** the folder "ios" to the location where you would like have the working site build.
    - **P.S.** If you are not working in the API, you can just delete that folder from build. Also in the docker-compose.yml file, delete lines 28-39 because you will not need to build the api container.
3. **Remove** the following items from the root directory.
    - `.git` folder (hidden)
    - `.gitignore` file (hidden)
4. **Unzip** the file called vendor in the app folder.

### Step 2 - Clone application repository from Github

1. In terminal, **navigate** to the app folder
2. **Clone** the repository using the following command:

```zsh
% git init
% git remote add origin https://github.com/WhatsUp247/wu247app.git
% git pull origin master
```

3. **Download** the autoload folder from this [Dropbox Folder](https://www.dropbox.com/sh/drbfam4qhmk1yin/AACkD1--83tuDjnTIbIJNeGUa?dl=0)
4. **Add** all files from _config_ folder to the repository in the folder _/app/config/autoload_ folder using this

### Step 3 - Application Build

1. **Build and Run** the container using the following command:

```zsh
% docker-compose up -d
```

2. **Check** that the container is running by using the following command:

```zsh
% docker ps
```

**Restart** the application container.

### Step 4 - Configure Database

1. **Access** the database's shell using Docker extention
2. **Access** MySQL with the following command

```zsh
% mysql
```

3. **Create** a user (replace brackets and content with your information)

```sql
> CREATE USER '[username]'@'%' IDENTIFIED BY '[password]';
```

4. **Give** administrative privileges using the commands below, inserting your own [username]:

```sql
> GRANT ALL PRIVILEGES ON * . * TO '[username]'@'%';
```

5. **Create** a database using the following command:

```sql
> CREATE DATABASE [database_name];
```

6. **Select** database:

```sql
> USE [database_name];
```

7. Import database from the zip file provided using this command:

```sql
> SOURCE /tmp/wu247-lab-backup.sql;
```

8. Type the following command to check that the database has been imported and make sure you see a user table listed:

```sql
> SHOW TABLES
```

### Step 5 - Configure Application

In the application folder _/app/config/autoload_, there are two files that need to be edited, _wu247model.global.php_ and _wu247model.local.php_.

#### Edit Global File

In the _wu247model.global.php_, we need to adjust the database name and the host name for **every** database option label `dsn`. You will need to replace [database_name] with the database name from the MySQL Container and replace [mysql_container_name] with the name of the MySQL Container.
**Find** the MySQL Container name by using the following command:

```zsh
% docker ps
```

Line example:

```php
'dsn' => 'mysql:dbname=[database_name];host=[mysql_container_name]',
```

#### Edit Local File

In the _wu247model.local.php_, we need to update **every** line of usernames and passwords to match your database user.

```php
'username' => '[username]',
'password' => '[password]',
```

**Restart** the application container.

### Step 6 - Confirm Application is Running Correctly

In your browser, view `localhost` and you should see the What's Up 24/7 web page.

## Windows
