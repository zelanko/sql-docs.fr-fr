---
title: "Mappage des Types de données XSD aux Types de données XPath (SQLXML 4.0) | Documents Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- XPath queries [SQLXML], mapping data types
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XPath data types [SQLXML]
- XSD schemas [SQLXML], mapping data types
ms.assetid: ced1a95e-18d4-4a5a-8da8-dbb6d58bbd45
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dae91d7e4c23c01d99de52c1ef6e1f1010bd081c
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2018
---
# <a name="mapping-xsd-data-types-to-xpath-data-types-sqlxml-40"></a>Mappage des types de données XSD en types de données XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
Quand une requête XPath est exécutée sur un schéma XSD et le type XSD est spécifié dans le **xsd : type** attribut, XPath utilise le type de données spécifié lors du traitement de la requête.  
  
 Le type de données Xpath d'un nœud est dérivé du type de données XSD dans le schéma, comme l'illustre le tableau ci-dessous. (Le nœud EmployeeID est utilisé à des fins d'illustration.)  
  
|Type de données XSD|Type de données XDR|Équivalent<br /><br /> Type de données XPath|SQL Server<br /><br /> conversion utilisée|  
|-------------------|-------------------|------------------------------------|--------------------------------------------|  
|**Base64Binary**<br /><br /> **HexBinary**|**Aucun**<br /><br /> **bin.base64bin.hex**|**Non applicable**|Aucun<br /><br /> EmployeeID|  
|**Booléen**|**boolean**|**boolean**|CONVERT(bit, EmployeeID)|  
|**Décimal, entier, float, byte, short, int, long, float, double, unsignedByte, unsignedShort, unsignedInt, unsignedLong**|**nombre, int, float, i1, i2, i4, i8, r4, r8ui1, ui2, ui4, ui8**|**number**|CONVERT(float(53), EmployeeID)|  
|**id, idref, idrefsentity, entities, notation, nmtoken, nmtokens, DateTime, string, AnyURI**|**id, idref, idrefsentity, entities, enumeration, notation, nmtoken, nmtokens, char, dateTime, dateTime.tz, string, uri, uuid**|**chaîne**|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|**decimal**|**fixed14.4**|**Non applicable (il n’est aucun type de données dans l’expression XPath qui est équivalent au type de données XDR fixed14.4).**|CONVERT(money, EmployeeID)|  
|**date**|**date**|**chaîne**|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|**time**|**time**<br /><br /> **time.tz**|**chaîne**|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
  
