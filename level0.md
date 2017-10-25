# Preparation

## Review attack cycle:

1. reconnaissance
2. scanning
3. exploitation
4. keeping access
5. removing tracks
6. use resource

##  scanning

Find information about software being used. In the case of HIWA, we made it
about as obvious as we can: there is a big logo on each page and a link that
takes the user to the about page. The about page has a link to the GitHub
repo.

## Common Application Vulnerabilities

* Default configuration

	In this case, the GitHub repo includes the code, as well as the
	default settings.

* Easy to guess default passwords

	Although I generally do not configure HIWA with admin/admin, I do add
	guest/guest and leune/leune.

* Web vulns

	* Unprotected directory indexes. Explained and then demonstrated by
		[http://compsci.adelphi.edu/~kees]

	* XSS. Demonstrated by inserting the following HTML snippets in
		[http://compsci.adelphi.edu/~kees/hello.php].

		<h1>Hello</h1>
		<blink>Irritating</blink>
		<script>document.location="http://google.com"</script>

		NOTE: May have to use Firefox, since Chrome commonly blocks 
		bad stuff.

	* SQL injection. Explained and then demonstrated by introducing the
		following HTML snippets to [http://compsci.adelphi.edu/~kees/db2.php]

		';--
		' or longitude=(select max(longitude) from zip);--
		' or 1=1;

# Exercise

Attack the application at [http://compsci.adelphi.edu/hiwa/login.php] and 
gain obtain the following objectives:

1. Gain access to the application

2. Add a user to the database with admin privs

3. Get free stuff!

4. Replace logo

# Answer

1. default creds (guest/guest) or SQLi (' or 1=1;--) in password field

2. Directory index and click on users.php, or select menu option

3. Add product with negative price

4. upload file called hiwa.png
