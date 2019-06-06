---
title: RecordCreateOptionsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordCreateOptionsEnum
helpviewer_keywords:
- RecordCreateOptionsEnum enumeration [ADO]
ms.assetid: 6d746670-0850-4065-9cd4-168dea1d3ea9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d57f1bc241e5e27618a9598895ea7be089ce20dd
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66712014"
---
# <a name="recordcreateoptionsenum"></a>RecordCreateOptionsEnum
Spécifie si un existant **enregistrement** doit être ouvert ou un nouveau **enregistrement** créé pour le [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet [Open](../../../ado/reference/ado-api/open-method-ado-record.md) (méthode). Les valeurs peuvent être combinées avec un opérateur AND.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adCreateCollection**|0x2000|Crée un **enregistrement** au niveau du nœud spécifié par *Source* paramètre, au lieu d’ouvrir un existant **enregistrement**. Si la source pointe vers un nœud existant, une erreur d’exécution se produit, sauf si **adCreateCollection** est combiné avec **adOpenIfExists** ou **adCreateOverwrite**.|  
|**adCreateNonCollection**|0|Crée un **enregistrement** de type [adSimpleRecord](../../../ado/reference/ado-api/recordtypeenum.md).|  
|**adCreateOverwrite**|0x4000000|Modifie les indicateurs de création **adCreateCollection**, **adCreateNonCollection**, et **adCreateStructDoc**. Quand ou est utilisé avec cette valeur et l’une des valeurs d’indicateur de création, si l’URL source pointe vers un nœud existant ou **enregistrement**, puis existant **enregistrement** est remplacé et un nouveau est créé à la place. Cette valeur ne peut pas être utilisée avec **adOpenIfExists**.|  
|**adCreateStructDoc**|0x80000000|Crée un **enregistrement** de type [adStructDoc](../../../ado/reference/ado-api/recordtypeenum.md), au lieu d’ouvrir un existant **enregistrement**.|  
|**adFailIfNotExists**|-1|Valeur par défaut. Génère une erreur d’exécution si *Source* pointe vers un nœud inexistant.|  
|**adOpenIfExists**|0x2000000|Modifie les indicateurs de création **adCreateCollection**, **adCreateNonCollection**, et **adCreateStructDoc**. Quand ou est utilisé avec cette valeur et l’une des valeurs d’indicateur de création, si l’URL source pointe vers un nœud existant ou **enregistrement** de l’objet, le fournisseur doit ouvrir existant **enregistrement** au lieu de créer un nouveau une. Cette valeur ne peut pas être utilisée avec **adCreateOverwrite**.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [Open, méthode (objet Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)
