---
title: Gestion des valeurs NULL (SQLXML)
description: 'Découvrez comment les attributs ou les éléments NULL peuvent être spécifiés dans un mise à jour SQLXML 4,0 à l’aide de l’attribut attribut updg : NullValue.'
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 7944369c409975eba2331fe12b55ec873dda61fd
ms.sourcegitcommit: 5c7634b007f6808c87094174b80376cb20545d5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84882168"
---
# <a name="null-handling-sqlxml-40"></a>gestion NULL (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La syntaxe XML assimile la valeur NULL à une absence. (Par exemple, si une valeur d’attribut ou d’élément est NULL, cet attribut ou cet élément est absent du document XML.) Dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML, l’attribut **attribut updg : NullValue** permet de spécifier null pour une valeur d’élément ou d’attribut.  
  
 Par exemple, la mise à jour suivante garantit que la valeur de **titre** pour un contact avec **ContactID** de 64 est null, puis met à jour la valeur de **titre** en « Mr ». pour ce contact.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync updg:nullvalue="IsNULL"  >  
    <updg:before>  
       <Person.Contact ContactID="64" Title="IsNULL" />  
    </updg:before>  
    <updg:after>  
       <Person.Contact ContactID="64" Title="Mr." />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Lorsque les paramètres sont transmis à un code de mise à jour (updategram), la valeur NULL peut être passée comme valeur de paramètre. Pour ce faire, spécifiez l’attribut **NullValue** dans le **\<updg:header>** bloc. Pour obtenir un exemple, consultez [transmission de paramètres à codes &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/passing-parameters-to-updategrams-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité mise à jour &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
