---
title: "Count, propriété (ADO) | Documents Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _Collection::Count
helpviewer_keywords:
- Count property [ADO]
ms.assetid: da9ccd1f-d402-41a2-940c-45556fc5340d
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 173b2fc9073676e77ad3068e9e9dc3ca76089702
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="count-property-ado"></a>Count, propriété (ADO)
Indique le nombre d’objets dans une collection.  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne un **Long** valeur.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **nombre** propriété pour déterminer le nombre d’objets dans une collection donnée.  
  
 Étant donné que la numérotation des membres d’une collection commence à zéro, vous devez toujours coder les boucles en commençant par le membre zéro et en terminant par la valeur de la **nombre** propriété moins 1. Si vous utilisez Microsoft Visual Basic et que vous souhaitez parcourir les membres d’une collection sans vérifier le **nombre** propriété, utilisez la **For Each... Suivant** commande.  
  
 Si le **nombre** propriété est zéro, il y a aucun objet dans la collection.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Collection d’axes (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[Collection de colonnes (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[Collection de CubeDefs (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[Collection de dimensions (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[Collection d’erreurs (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)|[Collection de champs (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[Collection de groupes (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[Collection de hiérarchies (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[Collection d’index (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[Collection de clés (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[Collection de niveaux (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[Collection de membres (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[Collection de paramètres (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)|[Collection de positions (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[Collection de procédures (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[Collection de propriétés (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)|[Collection de tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|[Collection d’utilisateurs (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[Collection de vues (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de propriété Count (VB)](../../../ado/reference/ado-api/count-property-example-vb.md)   
 [Exemple de propriété Count (VC ++)](../../../ado/reference/ado-api/count-property-example-vc.md)   
 [Refresh, méthode (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)

