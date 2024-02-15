# API-testing

API PENETRATION TESTING

Scenario given –

A Laravel Based Application named as “Generic University” is introduced that
contains vulnerable API . The job is to penetrate into the vulnerable API and
complete the tasks as given below:-

The purpose of this document is to extensively document the API penetration testing
activities carried out on the designated system. All assessments were performed in a
supervised environment with explicit authorization.

1. Find the emails of the administrator
2. Brute force the API to find new endpoints
3. Find out what grades everyone got in a class
4. Edit someone's grade
5. Make an account
6. Login to your account
7. Access admin API
8. Make your account an admin
9. Access the admin control panel
10. Delete everything
11. Restore everything

Task 1:

Find the emails of the administrator

Users with role-id: 1 are administrators.

So, the admin emails found are,

● ynitzsche@grant.com
● michel.hyatt@yahoo.com
● victoria.spencer@hotmail.com

Task 2:

Brute force the API to find new endpoints

By submitting 'API/users/' data to Intruder and designating 'users' as the field
for brute-forcing, diverse payloads are examined. This includes testing various
payload options such as 'class,' 'classes,' 'grades,' 'students,' 'admin,' 'marks,'
'university,' 'universities,' 'results,' 'email,' 'subject,' 'subjects,' 'teaches,' and
'grade book.'

During the attack, both status codes 200 and 404 are observed. A 200 status
indicates a successful endpoint, while 404 signifies an error.

Task 3:

Find out what grades everyone got in a class

Sending a GET request to '/api/grades' retrieves the complete set of grades
for all individuals within a class

Task 4:

Edit someone’s grade

It is done using PUT method by accessing the endpoints of specified user like
‘/api/grades/15’.This will retrieve the grades of id=15 and Include 'ContentType: application/json'
in the headers and add the following JSON payload:
{
…..
…
"grade": "70"
……
}


Task 5:

Make an account

Task 6:

Login to your account

Task 7:

Access admin API

Access the admin API by following these steps in BurpSuite:

i. In the Proxy section, review the history to find the 'home' URL.

ii. Select the 'home' entry and send it to the repeater tool.

iii. Modify the URL in the repeater to '/api/admin/'.

iv. Send the request. This action will grant access to the admin API


Task 8:

Make your account admin

i. Initiate a GET request to determine your account's 'role_id'.

ii. Once identified, modify this GET request to a PUT request targeting '/api/admin/22'.

iii. Add 'Content-Type: application/json' to the request headers.

iv. Include the JSON payload: { "role_id": 1 } to switch your account to admin status.

Task 9:

Access the admin control panel

To access the admin control panel through BurpSuite:

i. Navigate to the Proxy section and review the history.

ii. Select the 'home' URL entry and send it to the repeater tool.

iii. Modify the URL in the repeater to '/api/admin/'.

iv. Send the request. This action will grant access to the admin control panel

Task 10:

Delete everything

A GET request to '/api/admin/delete' will facilitate the deletion of all data.

Task 11:

Restore everything

A GET request to '/api/admin/restore' will facilitate the restoration of all
previously deleted data
