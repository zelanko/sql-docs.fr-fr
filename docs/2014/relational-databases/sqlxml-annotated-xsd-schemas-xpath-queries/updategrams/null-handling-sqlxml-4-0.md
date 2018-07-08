---
title: NULL (SQLXML 4.0) de gestion des | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- updg:nullvalue attribute
- updategrams [SQLXML], null values
- nullvalue attribute
- null values [SQLXML]
ms.assetid: 5e11eebb-d94e-4ce6-a6d0-870225706bc1
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fb61234696e419bc203822985f8966a81975e476
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172113"
---
# <a name="null-handling-sqlxml-40"></a>gestion NULL (SQLXML 4.0)
  La syntaxe XML assimile la valeur NULL à une absence. (Par exemple, si une valeur d'attribut ou d'élément est NULL, cet attribut ou élément est absent du document XML.) Dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML, l'attribut `updg:nullvalue` permet de spécifier NULL pour une valeur d'élément ou d'attribut.  
  
 Par exemple, la mise à jour suivant garantit que le **titre** valeur pour un contact avec **ContactID** de 64 est NULL et puis met à jour le **titre** valeur à « Mr. » pour ce contact.  
  
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
  
 Lorsque les paramètres sont transmis à un code de mise à jour (updategram), la valeur NULL peut être passée comme valeur de paramètre. Pour cela, spécifiez l'attribut `nullvalue` dans le bloc `<updg:header>`. Pour obtenir un exemple, consultez [transfert des paramètres aux codes &#40;SQLXML 4.0&#41;](passing-parameters-to-updategrams-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations de sécurité de mise à jour &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
