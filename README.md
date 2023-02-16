-- docker image download & run
docker pull mysql
docker run --name yong-mysql -e MYSQL_ROOT_PASSWORD=admin -d -p 3306:3306 mysql

-- schema sample download
wget https://github.com/datacharmer/test_db.git
git clone https://github.com/datacharmer/test_db.git
docker cp test_db/ yong-mysql:/

-- schema sample setup
docker exec -it yong-mysql bash
cd test_db
mysql -u root -p'admin' < employees.sql

-- connect mysql
mysql -u root -p'admin' -D employees
