---
title: "Prise en charge d’espace de noms en mode PATH | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 733d1a16e352403ca55053ea45a464591e92d7fb
ms.lasthandoff: 04/11/2017

---
# <a name="namespace-support-in-path-mode"></a>Prise en charge d'espace de noms en mode PATH
  La prise en charge des espaces de noms en mode PATH est fournie à l'aide de WITH NAMESPACES. Par exemple, la requête suivante démontre l'utilisation de la syntaxe WITH NAMESPACES pour déclarer un espace de noms ("a:") qui peut ensuite être utilisé dans l'instruction SELECT ultérieure :  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a>Exemples  
 Ces exemples montrent comment utiliser le mode PATH pour générer un document XML à partir d'une requête SELECT. Nombre de ces requêtes sont spécifiées par rapport aux documents XML des instructions de fabrication de bicyclettes stockés dans la colonne Instructions de la table ProductModel.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode PATH avec FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
