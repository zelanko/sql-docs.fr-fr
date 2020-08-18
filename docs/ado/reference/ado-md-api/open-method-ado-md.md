---
description: Open, méthode (ADO MD)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 56d6a216b7d21723d84d374b09a9c0b8c6c4806b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88440821"
---
# <a name="open-method-ado-md"></a>Open, méthode (ADO MD)
Récupère les résultats d’une requête multidimensionnelle et retourne les résultats à un [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Source*  
 facultatif. **Variante** qui prend la valeur d’une requête multidimensionnelle valide, telle qu’une requête MDX (Multidimensional Expression). L’argument *source* correspond à la propriété [source](../../../ado/reference/ado-md-api/source-property-ado-md.md) . Pour plus d’informations sur MDX, consultez la OLE DB pour la documentation sur le [traitement analytique en ligne (OLAP)](https://msdn.microsoft.com/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3) dans le kit de développement logiciel (SDK) Microsoft Data Access Components.  
  
 *ActiveConnection*  
 facultatif. **Variant** qui prend la valeur d’une chaîne spécifiant soit un nom de variable objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) ADO valide, soit une définition pour une connexion. L’argument *ActiveConnection* spécifie la connexion dans laquelle ouvrir l’objet [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) . Si vous transmettez une définition de connexion pour cet argument, ADO ouvre une nouvelle connexion à l’aide des paramètres spécifiés. L’argument *ActiveConnection* correspond à la propriété [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) .  
  
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
