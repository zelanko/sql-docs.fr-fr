---
title: 'Exemple : spécification de la directive CDATA | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- CDATA directive
ms.assetid: 949071e6-787f-480d-bb86-3ac16a027af1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b6c6c2f5e19e22cdff4b7f9ca282fc3406efd3fc
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664786"
---
# <a name="example-specifying-the-cdata-directive"></a>Exemple : spécification de la directive CDATA
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Si la directive a pour valeur **CDATA**, les données contenues ne sont pas encodées comme une entité, mais placées dans la section CDATA. Les attributs **CDATA** doivent être dépourvus de nom.  
  
 La requête suivante insère la description résumée des modèles de produits dans une section CDATA.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        ProductModelID  as [ProductModel!1!ProdModelID],  
        Name            as [ProductModel!1!Name],  
        '<Summary>This is summary description</Summary>'     
            as [ProductModel!1!!CDATA] -- no attribute name so ELEMENT assumed  
FROM    Production.ProductModel  
WHERE   ProductModelID=19  
FOR XML EXPLICIT  
```  
  
 Voici le résultat obtenu :  
  
```  
<ProductModel ProdModelID="19" Name="Mountain-100">  
   <![CDATA[<Summary>This is summary description</Summary>]]>  
</ProductModel>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode EXPLICIT avec FOR XML](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
