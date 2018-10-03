---
title: Modèles de contenu non déterministes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- non-deterministic content models
- content models [XML in SQL Server]
ms.assetid: 9d4513e7-dd19-4491-b7c7-28bc7c2f8589
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: df49312f86513e1860fbb3bc14cd33ca1edc845e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113756"
---
# <a name="non-deterministic-content-models"></a>modèles de contenu non déterministes
  Avant [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 (SP1), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rejetait les schémas XML qui avaient des modèles de contenu non déterministes.  
  
 À compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1, toutefois, les modèles de contenu non déterministes sont acceptés si les contraintes d’occurrence sont 0,1, ou non liées.  
  
## <a name="example-non-deterministic-content-model-rejected"></a>Exemple: modèle de contenu non déterministe rejeté  
 L'exemple suivant tente de créer un schéma XML dont le modèle de contenu est non déterministe. Le code échoue car il n'est pas certain si l'élément `<root>` doit avoir une séquence de deux éléments `<a>` ou si l'élément `<root>` doit avoir deux séquences, chacune possédant un élément `<a>` .  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="1" maxOccurs="2">  
                <element name="a" type="string" minOccurs="1" maxOccurs="2"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
 Il est possible de corriger le schéma en déplaçant la contrainte d'occurrence vers un emplacement unique. Par exemple, vous pouvez déplacer la contrainte vers la particule Sequence conteneur :  
  
```  
<sequence minOccurs="1" maxOccurs="4">  
    <element name="a" type="string" minOccurs="1" maxOccurs="1"/>  
</sequence>  
```  
  
 Ou vous pouvez la déplacer vers l'élément contenu :  
  
```  
<sequence minOccurs="1" maxOccurs="1">  
     <element name="a" type="string" minOccurs="1" maxOccurs="4"/>  
</sequence>  
```  
  
## <a name="example-non-deterministic-content-model-accepted"></a>Exemple: modèle de contenu non déterministe accepté  
 Le schéma suivant serait rejeté dans les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1.  
  
```  
CREATE XML SCHEMA COLLECTION MyCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema">  
    <element name="root">  
        <complexType>  
            <sequence minOccurs="0" maxOccurs="unbounded">  
                <element name="a" type="string" minOccurs="0" maxOccurs="1"/>  
                <element name="b" type="string" minOccurs="1" maxOccurs="unbounded"/>  
            </sequence>  
        </complexType>  
    </element>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications et limitations relatives aux collections de schémas XML sur le serveur](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
