# Solutions


### 1. Show the population of Germany
```sh
SELECT population 
FROM world 
WHERE name = 'Germany';
```

### 2. Show the name and the population for 'Sweden', 'Norway' and 'Denmark'
```sh
SELECT name, population
FROM world 
WHERE name IN ('Sweden', 'Norway', 'Denmark');
```

### 3. Show the names and areas for countries whose area is between 200000 and 250000
```sh
SELECT name, area FROM world
WHERE area BETWEEN 200000 AND 250000;
```