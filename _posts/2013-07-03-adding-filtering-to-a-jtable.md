---
layout: post
section-type: post
has-comments: true
title: 'Adding filtering to a JTable'
category: posts
tags: ['Java', 'Swing', 'UI']
---

To filter out rows in a JTable, you will need to add a RowFilter (javax.swing.RowFilter). This row filter takes a table model and an object that correspond to an entry in the model.

```
RowFilter<object,object> startsWithAFilter = new RowFilter<object,object>() {
   public boolean include(Entry entry) {
     for (int i = entry.getValueCount() - 1; i >= 0; i--) {
       if (entry.getStringValue(i).startsWith("a")) {
         // The value starts with "a", include it
         return true;
       }
     }
     // None of the columns start with "a"
     // return false so that this
     // entry is not shown
     return false;
   }
 };
```There are a few types of RowFilters available, like a generic “include” filter (so you specify which rows are to be included), a number/date/regex filter (which are specific RowFilter types) and an AND/OR/NOT filter to combine different row filters together.