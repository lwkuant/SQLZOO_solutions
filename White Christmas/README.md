# Solutions


### 1. Show the average daily temperature for August 10th 1964
```sh
SELECT ROUND(m8/10, 2) AS mean_temp
FROM hadcet
WHERE (yr = 1964) AND (dy = 10);
```

### 2. Show the twelve temperatures
```sh
SELECT (yr-1811) AS age, m12/10 AS mean_temp
FROM hadcet
WHERE (yr BETWEEN 1812 AND 1823) AND (dy = 25);
```

### 3. For each age 1-12 show which years where a White Christmas
```sh
SELECT (yr-1811) AS age, CASE WHEN MIN(m12/10)<0 THEN 'white' END AS wcc
FROM hadcet 
WHERE (yr BETWEEN 1812 AND 1823) AND (dy BETWEEN 21 AND 25)
GROUP BY age;
```

### 4. List all the years and the wcc for children born in each year of the data set. Only show years where the wcc was at least 7.
```sh
SELECT yb, COUNT(wcc)
FROM (
SELECT yb, yr-yb+1 AS age, CASE WHEN MIN(m12/10)<0 THEN 'white' END AS wcc
FROM hadcet
CROSS JOIN (
SELECT DISTINCT yr AS yb
FROM hadcet) AS temp_1
WHERE (yr BETWEEN yb+2 AND yb+11) AND (dy BETWEEN 21 AND 25)
GROUP BY yb, age) AS temp_2
GROUP BY yb
HAVING COUNT(wcc) >= 7;
```


