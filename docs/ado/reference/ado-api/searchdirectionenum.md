---
description: SearchDirectionEnum
title: SearchDirectionEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SearchDirectionEnum
helpviewer_keywords:
- SearchDirectionEnum enumeration [ADO]
ms.assetid: 81272ae3-2165-4f4e-adfe-9ede0368cb17
author: rothja
ms.author: jroth
ms.openlocfilehash: 918261998fec061f8f977a8a2dfc614166f564f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88442161"
---
# <a name="searchdirectionenum"></a>SearchDirectionEnum
Spécifie la direction d’une recherche d’enregistrement dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Constante|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adSearchBackward**|-1|Recherche vers le haut, en s’arrêtant au début du **jeu d’enregistrements**. Si aucune correspondance n’est trouvée, le pointeur d’enregistrement est positionné sur [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
|**adSearchForward**|1|Recherche en avant et en arrêt à la fin de l’ensemble d' **enregistrements**. Si aucune correspondance n’est trouvée, le pointeur d’enregistrement est positionné à [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constante|  
|--------------|  
|AdoEnums.SearchDirection.BACKWARD|  
|AdoEnums.SearchDirection.FORWARD|  
  
## <a name="applies-to"></a>S'applique à  
 [Find, méthode (ADO)](../../../ado/reference/ado-api/find-method-ado.md)
