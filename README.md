# SQLServer
Find the URL Reservation using
Get URL Reservation
````
netsh http show urlacl
````

It was due to SQL Reporting services having reserved the http://+:80/Reports url in http.sys.
I didn't actually have reporting services installed, but it apparently still reserved the url.

I fixed it with the following command:
````
netsh http delete urlacl url=http://+:80/Reports
````
