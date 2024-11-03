---
layout: post
section-type: post
has-comments: true
title: 'Paging queries (or querying large amounts of data) from a MySQL database in Java'
category: posts
tags: ['MySQL', 'Systems Administration', 'Web']
---

So I was trying to run a query of a large number of rows on a MySQL database using Java MySQL JDBC connectors, and I couldn't find an easy way to do this... so once I found out, I thought I'd post it here!

`Connection existingDBConn = DriverManager.getConnection("jdbc:mysql://databaseServerName:3306/databaseName","username","password"); Statement selectStatement = null; selectStatement = existingDBConn.createStatement(ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_READ_ONLY); selectStatement.setAutoCommit(false); selectStatement.setFetchSize(Integer.MIN_VALUE);`

`if (selectStatement.execute(selectSqlQuery)) { do { selectResultSet = selectStatement.getResultSet(); while (selectResultSet.next()) { System.out.println(selectResultSet.getString(1));// and so on......... whatever you'd do on each row of the database } } while (!((selectStatement.getMoreResults() == false) && (selectStatement.getUpdateCount() == -1))); }`

The things I needed to was to "setAutoCommit" to false and set the fetch size to "Integer.MIN\_VALUE".

Here's some of the references I used: - http://stackoverflow.com/questions/14535846/how-do-i-load-100-million-rows-in-to-memory - http://stackoverflow.com/questions/3682614/jdbc-how-to-read-all-rows-from-huge-table - http://dev.mysql.com/doc/refman/5.5/en/connector-j-reference-implementation-notes.html