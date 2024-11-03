---
layout: post
section-type: post
has-comments: true
title: 'Adding sorting to a JTable'
category: posts
tags: ['Java', 'Swing', 'UI']
---

[![sorter for JTable](http://anthonythecoder.files.wordpress.com/2013/06/sorter-for-jtable.png)](http://anthonythecoder.files.wordpress.com/2013/06/sorter-for-jtable.png)

To add buttons to a JTable’s headers so that when you click on the headers the JTable is sorted in those particular fields:

```
JTable table = new JTable();
table.setAutoCreateRowSorter(true);
```This is also helpful as the underlying TableModel is not altered. But to use selected cells one needs to use the following commands:```
//for column indices
table.convertColumnIndexToModel(viewColumnIndex);
table.convertColumnIndexToView(modelColumnIndex);

//for row indices
table.convertRowIndexToModel(viewRowIndex);
table.convertRowIndexToView(modelRowIndex);
Note that one can also extend off “DefaultTableModel” and add other helper functions to the table model such as row counts, column counts etc. Although do not include presentation layer concepts like “new entry rows” in the Table Model: these should be done in a separate JTable.


```