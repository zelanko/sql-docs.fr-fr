---
title: Position du catalogue (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog position
- catalog position [ODBC]
ms.assetid: 5bc5f64b-c75a-43d2-8745-102ec7a49000
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0305d978dc4ecd21892a0be3916fa5072b7be95a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303380"
---
# <a name="catalog-position"></a>Position du catalogue
La position d’un nom de catalogue dans un identifiant et la façon dont il est séparé du reste de l’identifiant varient d’une source de données à la source de données. Par exemple, dans une source de données Xbase, le nom du catalogue est un répertoire et, dans Microsoft® Windows®, est séparé du\\nom de table (qui est un nom de fichier) par un backslash ( ). L’illustration suivante démontre cette condition.  
  
 ![Position du catalogue : Xbase](../../../odbc/reference/develop-app/media/ch0801.gif "ch0801 ch0801")  
  
 Dans une source de données SQL Server, le catalogue est une base de données et est séparé du schéma et des noms de table par une période (.).  
  
 ![Position du catalogue : SQL Server](../../../odbc/reference/develop-app/media/ch0802.gif "ch0802 ch0802")  
  
 Dans une source de données Oracle, le catalogue est également la base de données, mais suit le nom de table et est séparé du schéma et des noms de table par un signe à l’affiche ( ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' ' '  
  
 ![Position du catalogue : Oracle](../../../odbc/reference/develop-app/media/ch0803.gif "ch0803 ch0803")  
  
 Pour déterminer le séparateur du catalogue et l’emplacement du nom du catalogue, une application appelle **SQLGetInfo** avec les options SQL_CATALOG_NAME_SEPARATOR et SQL_CATALOG_LOCATION. Les applications interopérables doivent construire des identifiants en fonction de ces valeurs.  
  
 Lorsque vous citez des identifiants qui contiennent plus d’une partie, les applications doivent prendre soin de citer chaque partie séparément et ne pas citer le caractère qui sépare les identifiants. Par exemple, la déclaration suivante pour sélectionner toutes les lignes et colonnes d’une table Xbase cite le catalogue (XBASE-SALES-CORP)\\et les noms de table (Parts.dbf), mais pas le séparateur du catalogue (  
  
```  
SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"  
```  
  
 La déclaration suivante pour sélectionner toutes les lignes et colonnes d’une table Oracle cite le catalogue (Ventes), schémas (Corporate) noms, mais pas le catalogue ou schéma (.) séparateurs:  
  
```  
SELECT * FROM "Corporate"."Parts"@"Sales"  
```  
  
 Pour plus d’informations sur la citation des identifiants, voir la section suivante, [Quoted Identifiers](../../../odbc/reference/develop-app/quoted-identifiers.md).
