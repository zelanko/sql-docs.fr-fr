---
description: PageSize, propriété (ADO)
title: PageSize, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::PageSize
helpviewer_keywords:
- PageSize property [ADO]
ms.assetid: e57930a6-46c4-4a17-a3b6-f79e94d5c9c7
author: rothja
ms.author: jroth
ms.openlocfilehash: 99365747e5049da4b8dd3cc58f58fd6e2a542e76
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442851"
---
# <a name="pagesize-property-ado"></a>PageSize, propriété (ADO)
Indique le nombre d’enregistrements constituant une page dans le [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **type long** qui indique le nombre d’enregistrements sur une page. La valeur par défaut est **10**.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **pageSize** pour déterminer le nombre d’enregistrements constituant une page logique de données. L’établissement d’une taille de page vous permet d’utiliser la propriété [AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md) pour accéder au premier enregistrement d’une page particulière. Cela est utile dans les scénarios de serveur Web lorsque vous souhaitez autoriser l’utilisateur à parcourir les données, en affichant un certain nombre d’enregistrements à la fois.  
  
 Cette propriété peut être définie à tout moment et sa valeur sera utilisée pour calculer l’emplacement du premier enregistrement d’une page particulière.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [AbsolutePage, PageCount et PageSize, propriétés, exemple (VB)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [AbsolutePage, PageCount et PageSize, propriétés, exemple (VC + +)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [AbsolutePage, propriété (ADO)](../../../ado/reference/ado-api/absolutepage-property-ado.md)   
 [PageCount, propriété (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)
