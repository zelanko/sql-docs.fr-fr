---
title: 'Exemple : spécification d’un élément racine pour les données XML générées par FOR XML | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RAW mode, specifying root element example
- RAW mode, with FOR XML example
ms.assetid: bcc54b11-0713-4e43-8dbe-d6f3ad1993b5
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 95efd8d52ec89c3184a882d32add5e17449d343d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141995"
---
# <a name="example-specifying-a-root-element-for-the-xml-generated-by-for-xml"></a>Exemple : spécification d'un élément racine pour les données XML générées par FOR XML
  En spécifiant l'option `ROOT` dans la requête `FOR XML` , vous pouvez demander un élément de niveau supérieur unique pour les données XML résultantes, comme illustré dans cette requête. L'argument spécifié pour la directive `ROOT` fournit le nom de l'élément racine.  
  
## <a name="example"></a>Exemple  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119 or ProductModelID=115  
FOR XML RAW, ROOT('MyRoot')  
go  
```  
  
 Voici le résultat obtenu :  
  
```  
<MyRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
  <row ProductModelID="115" Name="Cable Lock" />  
</MyRoot>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode RAW avec FOR XML](use-raw-mode-with-for-xml.md)  
  
  