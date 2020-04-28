---
title: Open, méthode (ADO MD) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Open
- Cellset::Open
helpviewer_keywords:
- Open method [ADO MD]
ms.assetid: a87d8080-a238-45e5-bc80-9a8625b3810f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 089fad427989c26ed1ed22ec3e9267297a29b820
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67949385"
---
# <a name="open-method-ado-md"></a>Open, méthode (ADO MD)
Récupère les résultats d’une requête multidimensionnelle et retourne les résultats à un [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Source*  
 Facultatif. **Variante** qui prend la valeur d’une requête multidimensionnelle valide, telle qu’une requête MDX (Multidimensional Expression). L’argument *source* correspond à la propriété [source](../../../ado/reference/ado-md-api/source-property-ado-md.md) . Pour plus d’informations sur MDX, consultez la OLE DB pour la documentation sur le [traitement analytique en ligne (OLAP)](https://msdn.microsoft.com/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3) dans le kit de développement logiciel (SDK) Microsoft Data Access Components.  
  
 *ActiveConnection*  
 Facultatif. **Variant** qui prend la valeur d’une chaîne spécifiant soit un nom de variable objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) ADO valide, soit une définition pour une connexion. L’argument *ActiveConnection* spécifie la connexion dans laquelle ouvrir l’objet [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) . Si vous transmettez une définition de connexion pour cet argument, ADO ouvre une nouvelle connexion à l’aide des paramètres spécifiés. L’argument *ActiveConnection* correspond à la propriété [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) .  
  
## <a name="remarks"></a>Notes  
 La méthode **Open** génère une erreur si l’un de ses paramètres est omis et que sa valeur de propriété correspondante n’a pas été définie avant la tentative d’ouverture de l’ensemble de **cellules**.  
  
## <a name="applies-to"></a>S'applique à  
 [Cellset, objet (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [CellSet, exemple (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [ActiveConnection, propriété (ADO MD)](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)   
 [Close, méthode (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Connection, objet (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Source, propriété (ADO MD)](../../../ado/reference/ado-md-api/source-property-ado-md.md)   
 [State, propriété (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
