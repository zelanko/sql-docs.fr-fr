---
title: Gestion des valeurs NULL (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
author: rothja
ms.author: jroth
ms.openlocfilehash: 430643e8a6c9bd3dd00b2763990645c6a162ee40
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047487"
---
# <a name="null-handling-sqlxml-40"></a>gestion NULL (SQLXML 4.0)
  La syntaxe XML assimile la valeur NULL à une absence. (Par exemple, si une valeur d’attribut ou d’élément est NULL, cet attribut ou cet élément est absent du document XML.) Dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML, l' `updg:nullvalue` attribut permet de spécifier null pour une valeur d’élément ou d’attribut.  
  
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
  
 Lorsque les paramètres sont transmis à un code de mise à jour (updategram), la valeur NULL peut être passée comme valeur de paramètre. Pour cela, spécifiez l'attribut `nullvalue` dans le bloc `<updg:header>`. Pour obtenir un exemple, consultez [transmission de paramètres à codes &#40;SQLXML 4,0&#41;](passing-parameters-to-updategrams-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité mise à jour &#40;SQLXML 4,0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
