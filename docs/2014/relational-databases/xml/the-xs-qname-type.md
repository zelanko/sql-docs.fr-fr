---
title: xs:QName, type | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xs:QName type
ms.assetid: 72c5bfde-b0b2-4372-bf36-97ba930dea06
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0904dc1a1e79c6f3669992bee19b7489bf0bce42
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227079"
---
# <a name="the-xsqname-type"></a>The xs:QName Type
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge les types dérivés de **xs:QName** utilisant un élément de restriction de schéma XML. De plus, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge actuellement les types union avec **QName** en tant que type de membre.  
  
## <a name="example"></a>Exemple  
 Les instructions `CREATE XML SCHEMA COLLECTION` suivantes ne peuvent pas charger le schéma XML, car elles spécifient le type `xs:QName` en tant que type de membre de l'union :  
  
```  
CREATE XML SCHEMA COLLECTION QNameLimitation1 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:int xs:QName"/>  
    </xs:simpleType>  
</xs:schema>'  
GO  
  
CREATE XML SCHEMA COLLECTION QNameLimitation2 AS N'  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="myUnion">  
        <xs:union memberTypes="xs:integer">  
   <xs:simpleType>  
    <xs:list itemType="xs:QName"/>  
   </xs:simpleType>  
  </xs:union>  
    </xs:simpleType>  
</xs:schema>'  
GO  
```  
  
 Ces deux instructions échouent avec une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications et limitations relatives aux collections de schémas XML sur le serveur](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
