---
title: Type mixte et contenu simple | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- mixed types [SQL Server]
ms.assetid: 6ea1f11d-e64b-4ebb-ab68-4eb6e4027665
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf0e4f54334d84aea5a33392655110374e893cc4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63241270"
---
# <a name="mixed-type-and-simple-content"></a>Type mixte et contenu simple
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge la restriction d'un type mixte à du contenu simple.  
  
## <a name="example"></a>Exemple  
 Dans la collection de schémas XML suivante, `myComplexTypeA` est un type complexe pouvant être vidé. Autrement dit, ses deux éléments ont `minOccurs` défini à 0. La tentative de restreindre ceci à du contenu simple, comme dans la déclaration `myComplexTypeB` , n'est pas prise en charge. Par conséquent, la création de la collection de schémas XML suivante échoue :  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://ns" xmlns:ns="http://ns"  
xmlns:ns1="http://ns1">  
  
    <complexType name="myComplexTypeA" mixed="true">  
        <sequence>  
            <element name="a" type="string" minOccurs="0"/>  
            <element name="b" type="string" minOccurs="0" maxOccurs="23"/>  
        </sequence>  
    </complexType>  
  
    <complexType name="myComplexTypeB">  
        <simpleContent>  
            <restriction base="ns:myComplexTypeA">  
                <simpleType>  
                    <restriction base="int">  
                        <minExclusive value="25"/>  
                    </restriction>  
                </simpleType>  
            </restriction>  
        </simpleContent>  
    </complexType>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications et limitations relatives aux collections de schémas XML sur le serveur](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
