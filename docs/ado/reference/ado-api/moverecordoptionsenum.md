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
ms.openlocfilehash: dcdb825073b267c3e3351001ecc7b11c969582e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932046"
---
# <a name="moverecordoptionsenum"></a>MoveRecordOptionsEnum
Spécifie le comportement de la méthode [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) de l’objet [Record](../../../ado/reference/ado-api/record-object-ado.md) .  
  
|Constant|Valeur|Description|  
|--------------|-----------|-----------------|  
|**adMoveUnspecified**|-1|valeur par défaut. Effectue l’opération de déplacement par défaut : l’opération échoue si le fichier ou le répertoire de destination existe déjà et que l’opération met à jour les liens hypertexte.|  
|**adMoveOverWrite**|1|Remplace le fichier ou le répertoire de destination, même s’il existe déjà.|  
|**adMoveDontUpdateLinks**|2|Modifie le comportement par défaut de la méthode **MoveRecord** en ne mettant pas à jour les liens hypertexte de l' **enregistrement**source. Le comportement par défaut dépend des fonctionnalités du fournisseur. L’opération de déplacement met à jour les liens si le fournisseur est en capacité. Si le fournisseur ne peut pas corriger les liens ou si cette valeur n’est pas spécifiée, le déplacement réussit même si les liens n’ont pas été résolus.|  
|**adMoveAllowEmulation**|4|Demande que le fournisseur tente de simuler le déplacement (à l’aide des opérations de téléchargement, de chargement et de suppression). Si la tentative de déplacement de l' **enregistrement** échoue parce que l’URL de destination se trouve sur un autre serveur ou sur un autre fournisseur que la source, cela peut entraîner une latence ou une perte de données accrue, en raison de différentes fonctionnalités du fournisseur lors du déplacement des ressources entre les fournisseurs.|  
  
## <a name="adowfc-equivalent"></a>Équivalent ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [MoveRecord, méthode (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
