---
title: Cellset, objet (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset
helpviewer_keywords:
- Cellset object [ADO MD]
ms.assetid: 5e2452c0-cac0-49b2-8099-836c35794d50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 57b570b93d4e8a6cf10d879659f0886e1c6f0c8e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601667"
---
# <a name="cellset-object-ado-md"></a>Cellset, objet (ADO MD)
Représente les résultats d’une requête multidimensionnelle. C’est un ensemble de cellules sélectionnées à partir de cubes ou d’autres ensembles de cellules.  
  
## <a name="remarks"></a>Notes  
 Données au sein d’un **Cellset** est récupéré à l’aide d’un accès direct de type tableau. Vous pouvez explorer un membre spécifique pour obtenir des données sur ce membre. Par exemple, le code suivant retourne la légende du premier membre dans la première position sur le premier axe d’un jeu de cellules nommé `cst`:  
  
```  
cst.Axes(0).Positions(0).Members(0).Caption  
```  
  
## <a name="remarks"></a>Notes  
 Il n’existe aucune notion d’une cellule en cours au sein d’un ensemble de cellules. Au lieu de cela, le [élément](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) propriété récupère un spécifique [cellule](../../../ado/reference/ado-md-api/cell-object-ado-md.md) objet à partir de l’ensemble de cellules. Les arguments de la **élément** propriété déterminent quelle cellule est récupérée. Vous pouvez spécifier la valeur ordinale unique d’une cellule. Vous pouvez également récupérer des cellules à l’aide de leur numéro de position le long de chaque axe de l’ensemble de cellules. Pour plus d’informations sur l’extraction des cellules, consultez le [élément](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) propriété.  
  
 Avec les collections, les méthodes et les propriétés d’un **Cellset** de l’objet, vous pouvez procédez comme suit :  
  
-   Associer une connexion ouverte avec un **Cellset** objet en définissant son [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) propriété.  
  
-   Exécuter et de récupérer les résultats d’une requête multidimensionnelle avec le [Open](../../../ado/reference/ado-md-api/open-method-ado-md.md) (méthode).  
  
-   Récupérer un **cellule** à partir de la **Cellset** avec la [élément](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) propriété.  
  
-   Retourner le [axe](../../../ado/reference/ado-md-api/axis-object-ado-md.md) objets qui définissent le **Cellset** avec la [Axes](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) collection.  
  
-   Récupérer des informations sur les dimensions utilisées pour filtrer les données dans le **Cellset** avec la [FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) propriété.  
  
-   Renvoyer ou spécifier la requête utilisée pour définir le **Cellset** avec la [Source](../../../ado/reference/ado-md-api/source-property-ado-md.md) propriété.  
  
-   Retourner l’état actuel de la **Cellset** (ouvertes, fermées, l’exécution ou connexion) avec le [état](../../../ado/reference/ado-md-api/state-property-ado-md.md) propriété.  
  
-   Fermez toute **Cellset** avec la [fermer](../../../ado/reference/ado-md-api/close-method-ado-md.md) (méthode).  
  
-   Récupérer des informations spécifiques au fournisseur sur le **Cellset** avec ADO standard [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés, méthodes et événements](../../../ado/reference/ado-md-api/cellset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple avec Cellset (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Axes, Collection (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)   
 [Cellule, objet (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Objet Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
