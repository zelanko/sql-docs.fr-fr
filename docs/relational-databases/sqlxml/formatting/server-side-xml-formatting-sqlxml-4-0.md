---
title: Mise en forme XML côté serveur (SQLXML)
description: Découvrez la mise en forme XML côté serveur des documents générés par les requêtes SQLXML 4,0 exécutées sur une base de données Microsoft SQL Server.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- FOR XML clause, formatting
- server-side XML formatting
ms.assetid: ae9ea068-0857-4505-a3b2-f53d256b644c
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 629221cc127011e63e58c5044ef9375001b68df3
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97429932"
---
# <a name="server-side-xml-formatting-sqlxml-40"></a>Mise en forme XML côté serveur (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Cette rubrique fournit des informations sur la mise en forme des documents XML sur le côté serveur des ensembles de lignes générés par les requêtes exécutées dans une base de données dans Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vous pouvez stocker et extraire des documents XML vers et depuis des tables de base de données. Pour extraire un document XML, utilisez l'extension de requête FOR XML dans une requête SELECT.  
  
 Par exemple, supposons qu’une application cliente exécute une commande sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui se compose de la [!INCLUDE[tsql](../../../includes/tsql-md.md)] requête suivante :  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
FOR XML AUTO  
```  
  
 Le serveur exécute la requête en deux étapes. D'abord, le serveur exécute cette instruction SELECT :  
  
```  
SELECT FirstName, LastName  
FROM   Person.Contact  
```  
  
 Le serveur applique ensuite la transformation FOR XML à l'ensemble de lignes généré. Les données XML obtenues sont alors transmises au client dans un ensemble de lignes d'une colonne. Dans cette documentation, ce processus est connu sous le nom de mise en forme XML côté serveur.  
  
 Côté serveur, vous pouvez spécifier les modes suivants avec une clause FOR XML :  
  
-   RAW  
  
-   AUTO  
  
-   EXPLICIT  
  
 Pour plus d’informations sur la clause FOR XML, consultez [construction de XML à l’aide de for XML](../../../relational-databases/xml/for-xml-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de la mise en forme XML côté client et côté serveur &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/formatting/architecture-of-client-side-and-server-side-xml-formatting-sqlxml-4-0.md)   
 [Mise en forme XML côté client &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)   
 [FOR XML &#40;SQL Server&#41;](../../../relational-databases/xml/for-xml-sql-server.md)  
  
  
