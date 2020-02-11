---
title: Prise en charge d’espace de noms en mode PATH | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ad1a6af717dcfa8ea42d9171e5ab23d9c24c6225
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63240786"
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
 [Utiliser le mode PATH avec FOR XML](use-path-mode-with-for-xml.md)  
  
  
