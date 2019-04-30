---
title: MoveRecordOptionsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- MoveRecordOptionsEnum
helpviewer_keywords:
- MoveRecordOptionsEnum enumeration [ADO]
ms.assetid: f53c2ce4-1021-4a45-92b8-775e8bebad99
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb86b01a42a097210801fd3654ff2af80df24e39
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63242448"
---
# <a name="moverecordoptionsenum"></a>MoveRecordOptionsEnum
Spécifie le comportement de la [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) (méthode).  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adMoveUnspecified**|-1|Valeur par défaut. Effectue l’opération de déplacement par défaut : L’opération échoue si le fichier de destination ou le répertoire existe déjà, et l’opération met à jour les liens hypertexte.|  
|**adMoveOverWrite**|1|Remplace le fichier de destination ou le répertoire, même si elle existe déjà.|  
|**adMoveDontUpdateLinks**|2|Modifie le comportement par défaut de **MoveRecord** méthode en mettant à jour ne pas de liens hypertexte de la source de **enregistrement**. Le comportement par défaut varie selon les capacités du fournisseur. Opération de déplacement met à jour les liens si le fournisseur est capable. Si le fournisseur ne peut pas réparer les liens ou si cette valeur n’est pas spécifiée, le déplacement réussit même lorsque des liens n'ont pas été résolus.|  
|**adMoveAllowEmulation**|4|Demande que le fournisseur essaie de simuler le déplacement (à l’aide de téléchargement, chargement, opérations et suppression). Si la tentative de déplacement le **enregistrement** échoue parce que l’URL de destination se trouve sur un autre serveur ou de prise en charge par un fournisseur autre que la source, cela peut entraîner une latence ou perte de données, en raison des caractéristiques différentes lorsque déplacement de ressources entre les fournisseurs.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [MoveRecord, méthode (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
