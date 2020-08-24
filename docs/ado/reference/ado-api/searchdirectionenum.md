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
ms.openlocfilehash: 13f8e73bc382493084c8d3712d4b7bda2ed35c13
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777528"
---
# <a name="searchdirectionenum"></a>SearchDirectionEnum
Spécifie la direction d’une recherche d’enregistrement dans un [Recordset](./recordset-object-ado.md).  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adSearchBackward**|-1|Recherche vers le haut, en s’arrêtant au début du **jeu d’enregistrements**. Si aucune correspondance n’est trouvée, le pointeur d’enregistrement est positionné sur [BOF](./bof-eof-properties-ado.md).|  
|**adSearchForward**|1|Recherche en avant et en arrêt à la fin de l’ensemble d' **enregistrements**. Si aucune correspondance n’est trouvée, le pointeur d’enregistrement est positionné à [EOF](./bof-eof-properties-ado.md).|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Package : **com. ms. wfc. Data**  
  
|Constant|  
|--------------|  
|AdoEnums.SearchDirection.BACKWARD|  
|AdoEnums.SearchDirection.FORWARD|  
  
## <a name="applies-to"></a>S'applique à  
 [Find, méthode (ADO)](./find-method-ado.md)