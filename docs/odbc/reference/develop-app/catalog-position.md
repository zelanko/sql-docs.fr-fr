---
description: Position du catalogue
title: Position du catalogue | Microsoft Docs
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
ms.openlocfilehash: 513c2449d296d167c499942636cbb94d637a2ede
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465961"
---
# <a name="catalog-position"></a>Position du catalogue
La position d’un nom de catalogue dans un identificateur et la façon dont il est séparé du reste de l’identificateur varient d’une source de données à une source de données. Par exemple, dans une source de données xBase, le nom du catalogue est un répertoire et, dans Microsoft® Windows®, est séparé du nom de la table (qui est un nom de fichier) par une barre oblique inverse ( \\ ). L’illustration suivante montre cette condition.  
  
 ![Position du catalogue : Xbase](../../../odbc/reference/develop-app/media/ch0801.gif "ch0801")  
  
 Dans une source de données SQL Server, le catalogue est une base de données et est séparé des noms de schéma et de table par un point (.).  
  
 ![Position du catalogue : SQL Server](../../../odbc/reference/develop-app/media/ch0802.gif "ch0802")  
  
 Dans une source de données Oracle, le catalogue est également la base de données, mais suit le nom de la table et est séparé des noms de schéma et de table par un arobase (@).  
  
 ![Position du catalogue : Oracle](../../../odbc/reference/develop-app/media/ch0803.gif "ch0803")  
  
 Pour déterminer le séparateur de catalogue et l’emplacement du nom de catalogue, une application appelle **SQLGetInfo** avec les options SQL_CATALOG_NAME_SEPARATOR et SQL_CATALOG_LOCATION. Les applications interopérables doivent construire des identificateurs en fonction de ces valeurs.  
  
 Lorsqu’il s’agit d’identifier des identificateurs qui contiennent plusieurs parties, les applications doivent veiller à citer chaque partie séparément et ne pas citer le caractère qui sépare les identificateurs. Par exemple, l’instruction suivante pour sélectionner toutes les lignes et les colonnes d’une table xbase met en guillemets les noms du catalogue (\XBASE\SALES\CORP) et de la table (parties. dbf), mais pas le séparateur de catalogue ( \\ ) :  
  
```  
SELECT * FROM "\XBASE\SALES\CORP"\"PARTS.DBF"  
```  
  
 L’instruction suivante permet de sélectionner toutes les lignes et les colonnes d’une table Oracle pour libeller les noms de catalogue (ventes), de schéma (d’entreprise) et de table (parties), mais pas les séparateurs de catalogue (@) ou de schéma (.) :  
  
```  
SELECT * FROM "Corporate"."Parts"@"Sales"  
```  
  
 Pour plus d’informations sur les identificateurs de guillemets, consultez la section suivante, [identificateurs entre guillemets](../../../odbc/reference/develop-app/quoted-identifiers.md).
