---
title: Mise en forme XML côté serveur (SQLXML)
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ec84fdfad468124f59cefde73486d5b19a5a4110
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75255898"
---
# <a name="server-side-xml-formatting-sqlxml-40"></a>Mise en forme XML côté serveur (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Cette rubrique fournit des informations sur la mise en forme des documents XML sur le côté serveur des ensembles de lignes générés par les requêtes exécutées dans une base de données dans Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], vous pouvez stocker et extraire des documents XML vers et depuis des tables de base de données. Pour extraire un document XML, utilisez l'extension de requête FOR XML dans une requête SELECT.  
  
 Par exemple, supposons qu’une application cliente exécute une [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] commande sur qui se compose [!INCLUDE[tsql](../../../includes/tsql-md.md)] de la requête suivante :  
  
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
  
  
