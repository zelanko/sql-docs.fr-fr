---
title: Noms de colonnes avec le chemin spécifié sous la forme data() | Microsoft Docs
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: 0b738e44-6108-4417-a9a4-abeb7680d899
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fcec69ca2f7d77f8f5bbdd298dfee3feb2d8c0d4
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68113177"
---
# <a name="column-names-with-the-path-specified-as-data"></a>Noms de colonnes avec le chemin d'accès spécifié sous la forme data()

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Si le chemin d'accès spécifié comme nom de colonne est « data() », la valeur est traitée en tant que valeur atomique dans le document XML généré. Un espace est ajouté au document XML si l'élément suivant dans la sérialisation est également une valeur atomique. Cela est utile lorsque vous créez une liste de valeurs d'élément et d'attribut de type liste. La requête suivante extrait l'ID de modèle, le nom et la liste des produits pour le modèle concerné.  
  
```sql
USE AdventureWorks2012;  
GO  
SELECT ProductModelID       AS "@ProductModelID",  
       Name                 AS "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
      FOR XML PATH (''))    AS "@ProductIDs"  
FROM  Production.ProductModel  
WHERE ProductModelID= 7   
FOR XML PATH('ProductModelData');  
```  
  
 L'instruction SELECT imbriquée extrait une liste d'ID de produit. Elle spécifie « data() » comme nom de colonne pour les ID de produit. Étant donné que le mode PATH spécifie une chaîne vide pour le nom d'élément de ligne, aucun élément de ligne n'est généré. À la place, les valeurs sont renvoyées comme étant affectées à un attribut ProductIDs de l’élément de ligne `<ProductModelData>` de l’instruction SELECT parente. Voici le résultat obtenu :  

```sql
<ProductModelData
  ProductModelID="7"
  ProductModelName="HL Touring Frame"
  ProductIDs="885 887 888 889 890 891 892 893"
/>
```

## <a name="see-also"></a>Voir aussi  
 [Utiliser le mode PATH avec FOR XML](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
