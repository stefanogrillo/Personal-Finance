# PER$ONAL FINANCE
#### Video Demo:  <URL https://youtu.be/4sMMOjQJ3Eg >
#### Description:

My web application follows the structure of Finance.

It first requires the user to subscribe, forcing the user to insert a password with constraints like: total lenght 8 characters, a lowercase letter, an uppercase letter, and a number. I used JavaScrypt to visualize to the user which constraints are met yet and which not. The password and the username will be stored in a specific SQL table where the password is encrypted.

![](https://github.com/stefanogrillo/Personal-Finance/blob/1e54fda381a3c3be9d48a637a760b8616b80a5e3/register.gif)

Once subscribed, the used can enter the web-app.

The first thing that will be visible is the Index page, where only the last five transactions are visible. Once there, the user can select the specific page he wants to visualize: (1) How to (includes (1.2) Modalities and (1.3) Categories), (2) Insert, (3) Graphs (includes (3.2) Modalities, (3.3) Categories and (3.4) Overtime), (4) History, (5) Change Password, and (6) Log Out. Before entering the app, there are also (7) Register and (8) Log In. In case of errors, the web-app shows the (9) Apology page.

## (1) How to - how1.html; how2.html
This section is shown as a dropdown menu, create with the aim of showing how to use the application. This means that the subcategories here presented are the list of (1.2) Modalities and (1.3) Categories. Both are simple HTML and CSS pages with no additional code. Modalities are "where" the transaction occurs, while Categories are the "motivation" for that transaction. Both lists are fixed for every user: the choice is constricted from two dedicated SQL tables, so that the user must only choose his/her own between the ones presented.<br>
Modalities are, for example, cash or debit cards. Categories are, for example, income coming from a gift, or an expense coming from utilities.

![](https://github.com/stefanogrillo/Personal-Finance/blob/1e54fda381a3c3be9d48a637a760b8616b80a5e3/modalities.gif)

![](https://github.com/stefanogrillo/Personal-Finance/blob/1e54fda381a3c3be9d48a637a760b8616b80a5e3/categories.gif)

## (2) Insert - add.html
Here the user actually chooses which input to insert in the web-app. This page is linked to the SQL database both from input, via Jinja (for the dropdown menu where the user has to select Modalities and Categories) and from output (the transaction is saved in the *Transaction table in SQL, which saves: id, users' id, date, modality, category, amount, total amount disposable to user).<br>
This page is made with Jinja (Python), HTML, CSS, and SQL.

## (3) Graphs - chart1.html; chart2.html; chart3.html
This section is a drop-down menu where the user can choose between three subcategories: (3.2) Modalities, (3.3) Categories and (3.4) Overtime. Modalities represents two graphs: a column chart where each modality is shown as a total amount of its relative transactions, and a pie chart where is easier to see the differences between the modalities. Data is directly inserted via Jinja from the SQL, to Python, to JavaScrypt. The datatypes created are Lists, and the JavaScrypt lybrary used is Chart.js.<br>
I used the same structure for the Categories, showing each category used as a column, and showing a recap in the pie chart.
Slightly different presentation occurs in the overtime graph: here I chose to use only one graph, a Line chart, where the whole timeline of transactions can be shown as the "total amount of income disposable to the user". I created this amount summing incomes and subtracting expenses as they occur in each transaction.
So, to recap, these pages are made with Jinja (Python), HTML, CSS, SQL, and JavaScrypt.

## (4) History - history.html
Here every transaction ever is shown whithin a table created with Jinja. Also, the overall disposable cash is displayed at the bottom.<br>
This page is made with Jinja (Python), SQL, HTML and CSS.

## (5) Change Password - change.html
Here the user has to reinsert his/her username and passwords, so that they can be checked inside the SQL database. As soon as they are confirmed (so that the user's account has not been hacked), the user is allowed to insert a new password, for teo times. The new password follows the same contraints as the one used to register. Once selected, it is inserted inside the SQL database (after being encrypted) instead of the old one.
This page is made with SQL, Python, HTML, CSS and JavaScrypt.

## (6) Log Out
Log out button from the application.

## (7) Register - register.html
Here the user is forced to follow a similar path to the one already seen in (5) Change Password. In this passage, the user inserts a username and a password, which follows the same constraints already seen. A JavaScrypt code is added to visualize to the user which constraints are already met.
This page is made with Jinja (Python), HTML, CSS, SQL, and JavaScrypt.

## (8) Log In - login.html
In this page the user actually enters the application. He/she has to insert username and password, which are checked whithin the SQL database, and in case of presence, the user is allowed to enter the web-app.
This page is made with Python, HTML, CSS, and SQL.

## (9) Apology - apology.html
This page is an auto-generated page that aims to show to the user that an error has occurred, but in a funny way. The Meme is updated with the text corresponding to the error occurred, which is written in Python and moved to HTML with Jinja.

## FILES
The projact follows the following Flask structure:<br>

~/project<br>
&emsp;   &emsp;   |__ /static<br>
&emsp;   &emsp;   &emsp;   &emsp;   |__ .css<br>
&emsp;   &emsp;   |__ /templates<br>
&emsp;   &emsp;   &emsp;   &emsp;   |__ .html<br>
&emsp;   &emsp;   |-- .py<br>
&emsp;   &emsp;   |-- .db<br>

The folder "Static" has inside only the CSS data needed. Other non utilized elements are the JavaScrypt lines of code, which are actually a selection of "might be useful in the future" codes. The actual JavaScrypt codes used are inserted in the specific Template with a "script" element.<br>
The Favicon is an idea of mine, taken directly from WhatsApp's emojies I guess.<br>
The file style.css is used to deliver the Navigation's Bar Brand as I wanted. It changes the color of the Brand to mimic the one used in Finance. Then an additional scrypt is added to visually improve the JavaScrypt code used in register.html and in change.html.

The JavaScrypt codes used in the serie of templates "chart.html" use data extracted from SQL via Python, and moved to JavaScrypt with Jinja (appropriately customized).

The folder "Templates" contains every template used in the web-app. The templates use all a common basis: the "layout.html" template, which is enlarged and refitted in each template using Jinja.

The remaining important files are app.py, where the back-end code is written in Python (using Flask), helpers.py, and personalfinance.db (the database in sqllite3).

In particular, the database has been created to maintain constant the number of Modalities and Categories for every user. To do so, two SQL tables have been created; the user can only choose which ones to use. As such, each transaction records the Modalities and Categories used but does not require the creation of a special custom list for the user.

Hope that you liked my project as much as I did, Thank You!
