# Visitors dashboard

From the book `Kubernetes operators` from Red Hat.

The Visitors Site tracks information about each request to its home page. Each time
the page is refreshed, an entry is stored with details about the client, backend server,
and timestamp. The home page displays a list of the most recent visits.

Components:

- web frontend in react
- rest api django
- database mysql