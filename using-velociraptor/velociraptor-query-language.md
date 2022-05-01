---
description: Understanding VQL is essential to the functionality and usage of Velociraptor.
---

# 🔎 Velociraptor Query Language

### What is a Query Language?

The purpose of a query language is to speed up the process of locating indicators of compromise (IOCs) and to make an analyst's job not only easier but also more practical. Many Digital Forensic and Incident Response (DFIR) frameworks have their own query languages for this purpose. The query language of <mark style="color:green;">Velociraptor</mark> is called: <mark style="color:green;">**Velociraptor Query Language**</mark> or <mark style="color:green;">**VQL**</mark>.&#x20;

### Using VQL

Before beginning threat hunting with <mark style="color:green;">**VQL**</mark>, a notebook is needed. Learn more about what a notebook is and how to set one up by using this documentation: [https://docs.velociraptor.app/docs/vql/notebooks/](https://docs.velociraptor.app/docs/vql/notebooks/)\
Notebooks are accessible via the tab on the left side navigation bar as shown below:

![Screenshot showing where to access Notebook w/Example Notebook](../.gitbook/assets/notebook\_1png.png)

<mark style="color:green;">**VQL**</mark> takes heavy inspiration from SQL in its design, for example it uses the same <mark style="color:blue;">`SELECT .. FROM .. WHERE`</mark>sentence structure. Unlike SQL, <mark style="color:green;">**VQL**</mark> does not require or allow a semicolon <mark style="color:blue;">`;`</mark> at the end of statements. <mark style="color:green;">**VQL**</mark> does not place any restrictions on the use of whitespace in the query body; In other words the following two statements are equivalent:&#x20;

```sql
-- This query is all on the same line - not very readable but valid.
LET X = SELECT * FROM info() SELECT * FROM X

-- Well indented query but VQL does not mind.
LET X= SELECT * FROM info()
SELECT * FROM X
```

Learn more about the specifics of each query and expanded usage from the official documentation, here: [https://docs.velociraptor.app/docs/vql/](https://docs.velociraptor.app/docs/vql/)

