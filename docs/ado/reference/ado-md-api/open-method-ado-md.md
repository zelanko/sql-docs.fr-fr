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
manager: jroth
ms.openlocfilehash: e22ab07f40ad6b4ef916d950909957b04c9d5be1
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66708718"
---
# <a name="open-method-ado-md"></a>Open, méthode (ADO MD)
Récupère les résultats d’une requête multidimensionnelle et renvoie les résultats vers un [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Cellset.Open Source, ActiveConnection  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Source*  
 Facultatif. Un **Variant** qui correspond à une requête multidimensionnelle valide, telles qu’une requête MDX (Multidimensional Expression). Le *Source* argument correspond à la [Source](../../../ado/reference/ado-md-api/source-property-ado-md.md) propriété. Pour plus d’informations sur MDX, consultez le [OLE DB pour OLAP Online Analytical Processing ()](https://msdn.microsoft.com/8a7673c6-3ca1-4411-9f1e-adf1e47df4f3) documentation dans Microsoft Data Access Components SDK.  
  
 *ActiveConnection*  
 Facultatif. Un **Variant** qui correspond à une chaîne spécifiant un ADO valide [connexion](../../../ado/reference/ado-api/connection-object-ado.md) de l’objet nom de variable ou une définition d’une connexion. Le *ActiveConnection* argument spécifie la connexion dans lequel ouvrir le [Cellset](../../../ado/reference/ado-md-api/cellset-object-ado-md.md) objet. Si vous transmettez une définition de la connexion pour cet argument, ADO ouvre une nouvelle connexion à l’aide des paramètres spécifiés. Le *ActiveConnection* argument correspond à la [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) propriété.  
  
## <a name="remarks"></a>Notes  
 Le **ouvrir** méthode génère une erreur si un de ses paramètres est omis et que sa valeur de propriété correspondante n’a pas été défini avant d’essayer d’ouvrir le **Cellset**.  
  
## <a name="applies-to"></a>S'applique à  
 [Cellset, objet (ADO MD)](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple avec Cellset (VB)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [ActiveConnection, propriété (ADO MD)](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md)   
 [Close, méthode (ADO MD)](../../../ado/reference/ado-md-api/close-method-ado-md.md)   
 [Objet Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Source, propriété (ADO MD)](../../../ado/reference/ado-md-api/source-property-ado-md.md)   
 [State, propriété (ADO MD)](../../../ado/reference/ado-md-api/state-property-ado-md.md)
