# SQL-Sandbox-Fun
Just messing around with sql


# This is a sql file that shows the basics.
```
CREATE DATABASE IF NOT EXISTS trainingDB;

USE trainingDB;

CREATE TABLE IF NOT EXISTS parent (
    first_name VARCHAR(20) NOT NULL,
    last_name VARCHAR(20) NOT NULL,
    address VARCHAR(100) NULL,
    age INT2 NOT NULL,
    PRIMARY KEY (parent_id)
)  ENGINE=INNODB;

CREATE DATABASE IF NOT EXISTS nflDB;

USE nflDB;

CREATE TABLE IF NOT EXISTS teams (
    team_name VARCHAR(20) NOT NULL,
    start_date DATETIME NOT NULL,
    end_date DATETIME NOT NULL,
    team_address VARCHAR(100) NULL,
    PRIMARY KEY (team_id)
)  ENGINE=INODB;

CREATE TABLE IF NOT EXISTS players (
    first_name VARCHAR(20) NOT NULL,
    last_name VARCHAR(20) NOT NULL,
    address VARCHAR(100) NULL,
    age INT2 NOT NULL,
    PRIMARY KEY (player_id),
    FOREIGN KEY (team_id) REFERENCES teams(team_id)
)  ENGINE=INODB;

INSERT INTO teams (team_name, start_date, end_date, team_address)
VALUES ('Tigers', STR_TO_DATE('1/12/1995'), STR_TO_DATE('7/25/2029'), '1234 my address');

INSERT INTO teams (team_name, start_date, end_date, team_address)
VALUES ('Dragons', STR_TO_DATE('5/9/1992'), STR_TO_DATE('5/20/2027'), '4567 my address');

INSERT INTO teams (team_name, start_date, end_date, team_address)
VALUES ('Dolphins', STR_TO_DATE('1/12/1995'), STR_TO_DATE('6/1/2022'), '7890 my address');

INSERT INTO players (first_name, last_name, age, team_id)
VALUES
('Ricky', 'Horton', 26, 1),
('Veron', 'Brock', 25, 2),
('Dianna', 'Clarke', 22, 2),
('Al', 'Vasquez', 30, 3),
('Maggie', 'Murphy', 28, 3),
('Norma', 'Tran', 29, 2),
('Arnold', 'Manning', 24, 1),
('Terrance', 'Mccormick', 25, 2),
('Elizabeth', 'Smith', 26, 1),
('Joyce', 'Maxwell', 27, 2),
('Megan', 'Morgan', 25, 3),
('Jerome', 'Rios', 23, 1),
('Melissa', 'Allison', 24, 2),
('Veronica', 'Parks', 25, 1),
('Thomas', 'Peters', 26, 3);

UPDATE players SET first_name = 'John', last_name = 'Smith';

# or use cascade
DELETE teams, players FROM teams
INNER JOIN players ON players.team_id = teams.team_id
where teams.team_id = 1;

CREATE DATABASE IF NOT EXISTS nbaDB;

USE nbaDB;

CREATE TABLE IF NOT EXISTS teams (
    team_name VARCHAR(20) NOT NULL,
    start_date DATETIME NOT NULL,
    end_date DATETIME NOT NULL,
    team_address VARCHAR(100) NULL,
    PRIMARY KEY (team_id)
)  ENGINE=INODB;

CREATE TABLE IF NOT EXISTS players (
    first_name VARCHAR(20) NOT NULL,
    last_name VARCHAR(20) NOT NULL,
    address VARCHAR(100) NULL,
    age INT2 NOT NULL,
    PRIMARY KEY (player_id),
    FOREIGN KEY (team_id) REFERENCES teams(team_id)
    FOREIGN KEY (city_id) REFERENCES cities(city_id)
)  ENGINE=INODB;

CREATE TABLE IF NOT EXISTS cities (
    city_name VARCHAR(20) NOT NULL,
    population INTEGER NOT NULL,
    details VARCHAR(100) NULL,
    state VARCHAR(40) NULL,
    PRIMARY KEY (city_id)
)  ENGINE=INODB;

INSERT INTO teams (team_name, start_date, end_date, team_address)
VALUES ('Tigers', STR_TO_DATE('1/12/1995'), STR_TO_DATE('7/25/2029'), '1234 my address');

INSERT INTO teams (team_name, start_date, end_date, team_address)
VALUES ('Dragons', STR_TO_DATE('5/9/1992'), STR_TO_DATE('5/20/2027'), '4567 my address');

INSERT INTO teams (team_name, start_date, end_date, team_address)
VALUES ('Dolphins', STR_TO_DATE('1/12/1995'), STR_TO_DATE('6/1/2022'), '7890 my address');

INSERT INTO players (first_name, last_name, age, team_id)
VALUES
('Ricky', 'Horton', 26, 1),
('Veron', 'Brock', 25, 2),
('Dianna', 'Clarke', 22, 2),
('Al', 'Vasquez', 30, 3),
('Maggie', 'Murphy', 28, 3),
('Norma', 'Tran', 29, 2),
('Arnold', 'Manning', 24, 1),
('Terrance', 'Mccormick', 25, 2),
('Elizabeth', 'Smith', 26, 1),
('Joyce', 'Maxwell', 27, 2),
('Megan', 'Morgan', 25, 3),
('Jerome', 'Rios', 23, 1),
('Melissa', 'Allison', 24, 2),
('Veronica', 'Parks', 25, 1),
('Thomas', 'Peters', 26, 3);

INSERT INTO cities (city_name, population, player_id) 
VALUES
('New York', 8175133),
('Los Ageles',3792621),
('Chicago', 2695598),
('Houston', 2099451),
('philadelphia',1547607),
('phoenix', 1488750),
('San Antonio', 1382951),
('Dallas', 1241162),
('Austin', 842592),
('Fort Worth', 777992);

UPDATE players SET first_name = 'John', last_name = 'Smith';

# or use cascade
DELETE teams, players FROM teams
INNER JOIN players ON players.team_id = teams.team_id
where teams.team_id = 1;
```
