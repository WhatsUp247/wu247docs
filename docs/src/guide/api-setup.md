# API Local Environment Setup

The API is built using Laminas API Tools. For documentaton about Laminas API Tools, check our their documentation: [https://api-tools.getlaminas.org/](https://api-tools.getlaminas.org/)

## Requirements

-   You need to have composer installed to your machine.
-   App's mysql container running

Please see the [composer.json](composer.json) file for list of packages.

## Setup Process

### Step 1 - Install Composer Dependencies

1. **Run** the following command:

```zsh
% composer install
```

Once you have the basic installation, you need to put it in development mode:

```zsh
% cd path/to/api/folder
% composer development-enable
```

### Step 2 - Build

1. **Add** API declaration to the docker-composer.yml

```yaml
api:
    build:
		context: ./api
		args:
			MYSQL_USER: ${MYSQL_USER}
			MYSQL_PASSWORD: ${MYSQL_PASSWORD}
    depends_on:
		- mysql
    ports:
		- "8080:80"
    volumes:
		- ./api:/var/www
```

2. **Run** the build

```zsh
% docker-compose up -d
```

3. **Visit** site at http://localhost:8080
