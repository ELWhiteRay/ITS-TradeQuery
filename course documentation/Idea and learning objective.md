Web-Based ITS that teaches introductory SQL through a business simulation. The learner manages a small trading company that buys products from suppliers, stores them in a warehouse, and fulfils customer orders.

To make business decisions, the learner writes SQL queries against the company’s database. The query results provide information for decisions like choosing a supplier, locating products or finding the correct employee for a specific task.

The target audience consist of learners with little or no prior SQL experience.

An intelligent tutoring system is benificial for learning SQL becuse beginners can make different types of mistakes, such as choosing the wrong table or using an incorrect condition. The system can give immediate feedback and offer hints based on the learner's current attempt. By connecting queries to business decisions, it also helps learners understand why the data is useful.

**Learning tasks**
--
The sysyem focuses on two SQL skills:
1)    Filtering data: retrieving relevant records with SELECT and WHERE.
2)    Joining tables: combining related information from two tables using JOIN.

Example tasks:
-       Find products with low stock.
-       Find available employees with correct sill.
-       Find supplier offers within a budget.
-       List products together with their suppliers.
-       Show customer orders together with customer information.
-       Show tasks together with assigned employees.

Exercise: *Finding misplaced products*
A delivery of products has arrived at the warehouse. Some products have been placed in the wrong storage zone. The learner must find all products that are currently in the *`electronics`* zone but should be stored in the *`fragile`* zone.
the *products* table contains the following data:

| id  | name       | current zone | required zone |     |     |
| --- | ---------- | ------------ | ------------- | --- | --- |
| 1   | lamp       | electronics  | fragile       |     |     |
| 2   | Headphones | electronics  | electronics   |     |     |
| 3   | Glass vase | fragile      | fragile       |     |     |
| 4   | LED        | electronics  | fragile       |     |     |
**Solution**
```SQL
SELECT name
FROM products
WHERE current_zone = 'electronics'
	AND required_zone = 'fragile';
```
**Expected result:**

| name |
| ---- |
| lamp |
| LED  |
The exercise practises filtering data with `WHERE` and combining two conditions with `AND`
**US: Find Misplaced Products**
As a learner who wants to learn SQL, i want to practise SQL queries by solving business tasks in a game, so that i can improve my SQL skills and earn more virtual money by making better decisions.

Acceptance criteria:
[ ] the system presents a business task and the relevant DB table
[ ] the learner system displays the query result and checks it against the expected result
[ ] the learner can request a hint when they are stuck
[ ] the system provides further hints if the learner needs more help 
[ ] the system confirms when the task is completed correctly
[ ] Completing the task allows the learner to continue the business scenario
[ ] the system records attempts and hint usage to identify skills that may need more practice

**System architecture and adaptation**
--
The system consists of four main components:
-       Domain model: SQL concepts, the company database, learning tasks and hints.
-       Student model: the learner’s attempts, results and use of hints for each skill.
-       Tutoring model: feedback on query results and context-sensitive hints. Additional practice would be offered for a skill that causes difficulties.
-       User interface: a browser-based interface with a task description, SQL editor, query results and a view of the company’s current situation.

Hints will be provided in stages, so the system may first suggest checking a filter and then identify a relevant table or column. When a specific error cannot be identified, it can provide a predefined hint for the task.

**Game scenario**
--
The initial prototype will contain one short scenario. The learner will inspect stock, compare supplier offers, and deal with a warehouse problem. For example, a delivery may be placed in the wrong storage zone and require sorting before it can be shipped. The learner can find an available employee with the appropriate skill and assign the task.

The game state will include a small set of values such as budget, stock, orders and employee availability.

![[gamePic.png]]

**Planned evaluation**
--
The system will be evaluated with participants who have little or no SQL experience. They will complete:

1.     Pre-test on two target skills.
2.     The learning scenario in the app.
3.     A post-test with comparable new tasks.

The evaluation will record task success, time, and hint usage. A potential research question is: how does learners’ performance on introductory SQL tasks change after using the tutorial in the app

The pre-/post-tests comparison can show changes in performance, but it cannot on its own establish whether adaptive hints caused an improvement.

**Technologies**
--
The interface is planned as a web application using HTM, CSS, JavaScript. The prototype will execute real SQL queries against a small database.


