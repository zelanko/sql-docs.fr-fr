---
title: Count, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Collection::Count
helpviewer_keywords:
- Count property [ADO]
ms.assetid: da9ccd1f-d402-41a2-940c-45556fc5340d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 292a4a8c26b3b10aa47fcbe7046a5897f601ed9f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919355"
---
# <a name="count-property-ado"></a>Count, propriété (ADO)
Indique le nombre d’objets dans une collection.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne une valeur de **type long** .  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **Count** pour déterminer le nombre d’objets dans une collection donnée.  
  
 Étant donné que la numérotation des membres d’une collection commence par zéro, vous devez toujours coder les boucles en commençant par le membre zéro et en terminant par la valeur de la propriété **Count** moins 1. Si vous utilisez Microsoft Visual Basic et souhaitez parcourir les membres d’une collection sans vérifier la propriété Count, utilisez l' **argument** **for each... Commande suivante** .  
  
 Si la propriété **Count** est égale à zéro, la collection ne contient aucun objet.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Axes, collection (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Columns, collection (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs, collection (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Dimensions, collection (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Errors, collection (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)|[Fields, collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Groups, collection (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Hierarchies, collection (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Indexes, collection (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Keys, collection (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Levels, collection (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Members, collection (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Parameters, collection (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Positions, collection (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Procedures, collection (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)|[Tables, collection (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|[Users, collection (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Views, collection (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>Voir aussi  
 [Count, exemple de propriété (VB)](../../../ado/reference/ado-api/count-property-example-vb.md)   
 [Count, exemple de propriété (VC + +)](../../../ado/reference/ado-api/count-property-example-vc.md)   
 [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)
