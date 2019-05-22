---
title: Mappage des Types de données XSD aux Types de données XPath (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
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
author: MightyPen
ms.author: genemi
ms.reviewer: ''
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f10134d4aa4d71c4471e5e3120b3f8fbd8ee1748
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65980784"
---
# <a name="mapping-xsd-data-types-to-xpath-data-types-sqlxml-40"></a>Mappage des types de données XSD en types de données XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Quand une requête XPath est exécutée sur un schéma XSD et le type XSD est spécifié dans le **xsd : type** attribut, XPath utilise le type de données spécifié lorsqu’il traite la requête.  
  
 Le type de données Xpath d'un nœud est dérivé du type de données XSD dans le schéma, comme l'illustre le tableau ci-dessous. (Le nœud EmployeeID est utilisé à des fins d'illustration.)  
  
|Type de données XSD|Type de données XDR|Équivalent<br /><br /> Type de données XPath|SQL Server<br /><br /> conversion utilisée|  
|-------------------|-------------------|------------------------------------|--------------------------------------------|  
|**Base64Binary**<br /><br /> **HexBinary**|**Aucun**<br /><br /> **bin.base64bin.hex**|**Non applicable**|None<br /><br /> EmployeeID|  
|**Booléen**|**boolean**|**boolean**|CONVERT(bit, EmployeeID)|  
|**Decimal, integer, float, byte, short, int, long, float, double, unsignedByte, unsignedShort, unsignedInt, unsignedLong**|**number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8**|**nombre**|CONVERT(float(53), EmployeeID)|  
|**id, idref, idrefsentity, entities, notation, nmtoken, nmtokens, DateTime, string, AnyURI**|**id, idref, idrefsentity, entities, enumeration, notation, nmtoken, nmtokens, char, dateTime, dateTime.tz, string, uri, uuid**|**chaîne**|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|**decimal**|**fixed14.4**|**Non applicable (il n’est aucun type de données dans XPath est équivalente au type de données XDR fixed14.4).**|CONVERT(money, EmployeeID)|  
|**date**|**date**|**chaîne**|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|**time**|**time**<br /><br /> **time.tz**|**chaîne**|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
  
