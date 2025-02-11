---
description: "Learn more about: How to: Store and Reuse Queries"
title: "How to: Store and Reuse Queries"
ms.date: "03/30/2017"
dev_langs: 
  - "csharp"
  - "vb"
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
---
# How to: Store and Reuse Queries

When you have an application that executes structurally similar queries many times, you can often increase performance by compiling the query one time and executing it several times with different parameters. For example, an application might have to retrieve all the customers who are in a particular city, where the city is specified at runtime by the user in a form. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports the use of *compiled queries* for this purpose.  
  
> [!NOTE]
> This pattern of usage represents the most common use for compiled queries. Other approaches are possible. For example, compiled queries can be stored as static members on a partial class that extends the code generated by the designer.  
  
## Example 1

 In many scenarios you might want to reuse the queries across thread boundaries. In such cases, storing the compiled queries in static variables is especially effective. The following code example assumes a `Queries` class designed to store compiled queries, and assumes a Northwind class that represents a strongly typed <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## Example 2  

 You cannot currently store (in static variables) queries that return an *anonymous type*, because type has no name to provide as a generic argument. The following example shows how you can work around the issue by creating a type that can represent the result, and then use it as a generic argument.  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## See also

- <xref:System.Data.Linq.CompiledQuery>
- [Query Concepts](query-concepts.md)
- [Querying the Database](querying-the-database.md)
