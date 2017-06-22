---
title: "Type mixte et contenu simple | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mixed types [SQL Server]
ms.assetid: 6ea1f11d-e64b-4ebb-ab68-4eb6e4027665
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4c6ca3595ced1ff8d74c625d25e507b246f84342
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

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
 [Spécifications et limitations relatives aux collections de schémas XML sur le serveur](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
