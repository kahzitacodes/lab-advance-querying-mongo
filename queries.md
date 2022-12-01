![Ironhack Logo](https://i.imgur.com/1QgrNNw.png)

# Answers

### 1. All the companies whose name match 'Babelgum'. Retrieve only their `name` field.

**`query`**: /_{name: "Babelgum"}_/

### 2. All the companies that have more than 5000 employees. Limit the search to 20 companies and sort them by **number of employees**.

**`query`**: _{ number_of_employees: { $gt: 5000 } }_
**`sort`**: _{ number_of_employees: 1 }_
**`limit`**: _20_

### 3. All the companies founded between 2000 and 2005, both years included. Retrieve only the `name` and `founded_year` fields.

**`query`**: _{ $and: [ { founded_year: { $gte: 2000 } }, { founded_year: { $lte: 2005 }} ] }_
**`projection`**: _{ name: 1, founded_year: 1}_

### 4. All the companies that had a Valuation Amount of more than 100.000.000 and have been founded before 2010. Retrieve only the `name` and `ipo` fields.

**`query`**: _{ $and: [ { founded_year: { $lt: 2010}}, { "ipo.valuation_amount": {$gt: 100000000}} ] }_
**`projection`**: _{ name: 1, ipo: 1}_

### 5. All the companies that have less than 1000 employees and have been founded before 2005. Order them by the number of employees and limit the search to 10 companies.

**`query`**: _{ $and: [ { number_of_employees: { $lt: 1000 } }, { founded_year: { $lt: 2005 } } ] }_
**`sort`**: _{ number_of_employees: 1 }_
**`limit`**: _10_

### 6. All the companies that don't include the `partners` field.

**`query`**: _{ partners: { $ne: [] } }_

### 7. All the companies that have a null type of value on the `category_code` field.

**`query`**: _{category_code: {$not:{$type: "null"}}}_

### 8. All the companies that have at least 100 employees but less than 1000. Retrieve only the `name` and `number of employees` fields.

**`query`**: _{ number_of_employees: {$gt: 100, $lt: 1000} }_
**`projection`**: _{name: 1, number_of_employees: 1}_

### 9. Order all the companies by their IPO price in a descending order.

**`query`**: _{ipo: {$not:{$type: "null"}}}_
**`sort`**: _{"ipo.valuation_amount": -1}_

### 10. Retrieve the 10 companies with most employees, order by the `number of employees`

**`query`**: _{number_of_employees: -1}_
**`limit`**: _10_

### 11. All the companies founded on the second semester of the year. Limit your search to 1000 companies.

**`query`**: _{founded_month: {$gte: 6, $lte: 12 }}_
**`limit`**: _1000_

### 12. All the companies founded before 2000 that have an acquisition amount of more than 10.000.000

**`query`**: _{$and: [{founded_year: {$lt: 2000}}, {"acquisition.price_amount": {$gt: 10000000}}]}_

### 13. All the companies that have been acquired after 2010, order by the acquisition amount, and retrieve only their `name` and `acquisition` field.

**`query`**: _{$and: [{founded_year: {$gt: 2010}}, {acquisition: {$ne: null}}]}_
**`projection`**: _{name: 1, acquisition: 1}_
**`sort`**: _{acquisition: 1}_

### 14. Order the companies by their `founded year`, retrieving only their `name` and `founded year`.

**`query`**: _{founded_year: {$ne: null}}_
**`projection`**: _{name: 1, founded_year: 1}_
**`sort`**: _{founded_year: 1}_

### 15. All the companies that have been founded on the first seven days of the month, including the seventh. Sort them by their `acquisition price` in a descending order. Limit the search to 10 documents.

**`query`**: _{founded_day: {$lte: 7}}_
**`sort`**: _{"acquisition.acquisition_price": 1}_
**`limit`**: _10_

### 16. All the companies on the 'web' `category` that have more than 4000 employees. Sort them by the amount of employees in ascending order.

**`query`**: _{$and: [{category_code: "web"}, {number_of_employees: {$gt: 4000}}]}_
**`sort`**: _{number_of_employees: 1}_

### 17. All the companies whose acquisition amount is more than 10.000.000, and currency is 'EUR'.

**`query`**: _{$and: [{"acquisition.price_currency_code": "EUR"}, {"acquisition.price_amount": {$gt: 10000000}}]}_

### 18. All the companies that have been acquired on the first trimester of the year. Limit the search to 10 companies, and retrieve only their `name` and `acquisition` fields.

**`query`**: _{"acquisition.acquired_month": {$gte: 1, $lte: 3 }}_
**`projection`**: _{name: 1, acquisition: 1}_
**`limit`**: _10_

### 19. All the companies that have been founded between 2000 and 2010, but have not been acquired before 2011.

**`query`**: _{$and: [{founded_year: {$gte: 2000, $lte: 2010}}, {"acquisition.acquired_year": { $gt: 2011 }}]}_
