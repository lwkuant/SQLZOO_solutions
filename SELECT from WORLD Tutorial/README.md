# Solutions


### 1. Show the name, continent and population of all countries
```sh
SELECT name, continent, population
FROM world;
```

### 2. Show the name of the countries which have a population of at least 200000000
```sh
SELECT name
FROM world 
WHERE population >= 200000000;
```

### 3. Show the name and per capita GDP for those countries with a population of at least 200000000
```sh
SELECT name, (gdp/population) AS per_cap_gdp
FROM world
WHERE population >= 200000000
ORDER BY per_cap_gdp DESC;
```

### 4. Show the name and population in millions for the countries located in South America
```sh
SELECT name, population/1000000 AS pop_million
FROM world 
WHERE continent = 'South America'
ORDER BY pop_million DESC;
```

### 5. Show the name and population for France, Germany and Italy
```sh
SELECT name, population 
FROM world 
WHERE name IN ('France', 'Germany', 'Italy');
```

### 6. Show the countries which have a name that includes the word 'United'
```sh
SELECT name 
FROM world 
WHERE name LIKE '%United%';
```

### 7. Show the countries that are big by area or big by population. Show name, population and area
```sh
SELECT name, population, area 
FROM world 
WHERE (area > 3000000) OR (population > 250000000)
ORDER BY area DESC, population DESC;
```

### 8. Show the countries that are big by area or big by population but not both. Show name, population and area
```sh
SELECT name, population, area 
FROM world 
WHERE (area > 3000000) XOR (population > 250000000)
ORDER BY area DESC, population DESC;
```

### 9. For South America show population in millions and GDP in billions both to 2 decimal places
```sh
SELECT name, ROUND(population/1000000, 2) AS pop, ROUND(gdp/1000000000, 2) AS gdp
FROM world 
WHERE continent = 'South America'
ORDER BY pop DESC, gdp DESC;
```

### 10. Show per-capita GDP for the trillion dollar countries to the nearest $1000
```sh
SELECT name, ROUND(gdp/population, -3) AS gdp_per_cap
FROM world 
WHERE gdp >= 1000000000000;
```

### 11. Show the name and capital where the name and the capital have the same number of characters
```sh
SELECT name, capital 
FROM world 
WHERE (LENGTH(name) = LENGTH(capital))
ORDER BY LENGTH(name);
```

### 12. Show the name and the capital where the first letters of each match. Don't include countries where the name and the capital are the same word
```sh
SELECT name, capital 
FROM world 
WHERE (LEFT(name, 1) = LEFT(capital, 1)) AND (name != capital);
```

### 13. Find the country that has all the vowels and no spaces in its namecapital are the same word
```sh
SELECT name
FROM world 
WHERE (name LIKE '%a%') AND
(name LIKE '%e%') AND
(name LIKE '%i%') AND
(name LIKE '%o%') AND
(name LIKE '%u%') AND
(name NOT LIKE '% %');
```