---
title: "Définir le classement d’une Dimension | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OrderBy property
- dimensions [Analysis Services], ordering
- Business Intelligence enhancements [Analysis Services], ordering
- dimensions [Analysis Services], Business Intelligence enhancements
- ordering dimensions [Analysis Services]
- OrderByAttributeID property
ms.assetid: c42fbd58-244d-4e0a-b715-6f919cbc3ad9
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 879c7266c06551aa040a075e4af4ed537e58cab9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="bi-wizard---define-the-ordering-for-a-dimension"></a>Assistant BI - définir le classement d’une Dimension
  Ajoutez la fonctionnalité de classement des attributs à un cube ou à une dimension pour spécifier comment les membres d'un attribut sont classés. Les membres peuvent être classés d'après le nom ou la clé de l'attribut, ou d'après le nom ou la clé d'un autre attribut (en fonction d'une relation d'attribut). Par défaut, les membres sont classés d'après le nom de l'attribut. Cette fonctionnalité modifie les paramètres de propriété **OrderBy** et **OrderByAttributeID** des attributs d'une dimension.  
  
 Pour ajouter la fonctionnalité de classement des attributs, utilisez l'Assistant Business Intelligence et sélectionnez l'option **Spécifier l'ordre des attributs** dans la page **Choisir des améliorations** . Cet Assistant vous guide ensuite dans la procédure à suivre pour sélectionner la dimension à laquelle vous voulez appliquer le classement des attributs et pour spécifier le classement à utiliser pour les attributs de la dimension sélectionnée.  
  
## <a name="selecting-a-dimension"></a>Sélection d'une dimension  
 Dans la première page **Spécifier l'ordre des attributs** de l'Assistant, vous spécifiez la dimension à laquelle vous voulez appliquer le classement des attributs. L'ajout de la fonctionnalité de classement des attributs à la dimension sélectionnée apportera des modifications à cette dimension. Ces modifications seront héritées par tous les cubes contenant la dimension sélectionnée.  
  
## <a name="specifying-ordering"></a>Spécification du classement  
 Dans la deuxième page **Spécifier l'ordre des attributs** de l'Assistant, vous spécifiez comment tous les attributs de la dimension vont être classés.  
  
 Dans la colonne **Attribut de classement** , vous pouvez modifier l'attribut utilisé pour effectuer le classement. Si l’attribut que vous souhaitez utiliser pour classer les membres n’est pas dans la liste, faites défiler la liste, puis  **\<nouvel attribut... >** pour ouvrir le **sélectionner une colonne** boîte de dialogue, dans laquelle vous pouvez sélectionner une colonne dans une table de dimension. En sélectionnant une colonne à l'aide de la boîte de dialogue **Sélectionner une colonne** , vous allez créer un attribut supplémentaire qui servira à classer les membres d'un attribut.  
  
 Dans la colonne **Critères** , vous pouvez ensuite choisir si les membres de l'attribut doivent être classés par **Clé** ou par **Nom**.  
  
  

