---
title: Mappage de types de données XSD à des types de données XPath (SQLXML)
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
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6b956bf3a52b9ae14e59af770d279e8be8fec028
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75257384"
---
# <a name="mapping-xsd-data-types-to-xpath-data-types-sqlxml-40"></a>Mappage des types de données XSD en types de données XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Lorsqu’une requête XPath est exécutée sur un schéma XSD et que le type XSD est spécifié dans l’attribut **xsd : type** , XPath utilise le type de données spécifié lors du traitement de la requête.  
  
 Le type de données Xpath d'un nœud est dérivé du type de données XSD dans le schéma, comme l'illustre le tableau ci-dessous. (Le nœud EmployeeID est utilisé à des fins d'illustration.)  
  
|Type de données XSD|Type de données XDR|Équivalent<br /><br /> Type de données XPath|SQL Server<br /><br /> conversion utilisée|  
|-------------------|-------------------|------------------------------------|--------------------------------------------|  
|**Base64Binary**<br /><br /> **HexBinary**|**None**<br /><br /> **bin. base64bin. hex**|**Non applicable**|Aucune<br /><br /> EmployeeID|  
|**Boolean**|**expression**|**expression**|CONVERT(bit, EmployeeID)|  
|**Decimal, Integer, float, Byte, Short, int, long, float, double, unsignedByte, unsignedShort, unsignedInt, unsignedLong**|**number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8**|**certain**|CONVERT(float(53), EmployeeID)|  
|**ID, IDREF, idrefsentity, Entities, notation, NMTOKEN, NMTOKENS, DateTime, String, anyURI**|**ID, IDREF, idrefsentity, Entities, énumération, notation, NMTOKEN, NMTOKENS, Char, dateTime, dateTime.tz, String, Uri, UUID**|**chaîne**|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|**sépar**|**fixed14.4**|**Non applicable (il n’y a pas de type de données dans XPath qui est équivalent au type de données. 14,4 XDR fixe.)**|CONVERT(money, EmployeeID)|  
|**Date**|**Date**|**chaîne**|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|**simultanément**|**simultanément**<br /><br /> **time.tz**|**chaîne**|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
  
