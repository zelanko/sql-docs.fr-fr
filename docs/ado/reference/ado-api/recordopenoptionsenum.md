---
title: RecordOpenOptionsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordOpenOptionsEnum
helpviewer_keywords:
- RecordOpenOptionsEnum enumeration [ADO]
ms.assetid: 9028aba4-90fc-4dfc-88e4-fa8a7b6fedee
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c0ed637d8e77ef7fc152f994da81db010fa80900
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66712154"
---
# <a name="recordopenoptionsenum"></a>RecordOpenOptionsEnum
Spécifie les options pour l’ouverture une [enregistrement](../../../ado/reference/ado-api/record-object-ado.md). Ces valeurs peuvent être combinées à l’aide d’ou.  
  
|Constante|Value|Description|  
|--------------|-----------|-----------------|  
|**adDelayFetchFields**|0x8000|Indique au fournisseur que les champs associés le **enregistrement** ne doivent pas être récupérée au départ, mais peut être extrait à la première tentative d’accéder au champ. Le comportement par défaut, indiqué par l’absence de cet indicateur, consiste à récupérer tous les **enregistrement** champs d’objet.|  
|**adDelayFetchStream**|0x4000|Indique au fournisseur qui le flux par défaut associé le **enregistrement** ne doivent pas être récupéré initialement. Le comportement par défaut, indiqué par l’absence de cet indicateur, consiste à récupérer le flux par défaut associé à la **enregistrement** objet.|  
|**adOpenAsync**|0x1000|Indique que le **enregistrement** objet est ouvert en mode asynchrone.|  
|**adOpenExecuteCommand**|0x10000|Indique que la chaîne Source contient le texte de la commande qui doit être exécuté. Cette valeur est équivalente à la **adCmdText** option **Recordset.Open**.|  
|**adOpenRecordUnspecified**|-1|Valeur par défaut. Indique aucune option n’est spécifiée.|  
|**adOpenOutput**|0x800000|Qui indique si la source pointe sur un nœud qui contient un script exécutable (comme un. Page ASP), puis l’ouvert **enregistrement** contiendra les résultats du script exécuté. Cette valeur est uniquement valide avec les enregistrements sans collection.|  
  
## <a name="adowfc-equivalent"></a>Équivalent de ADO/WFC  
 Ces constantes n’ont pas d’équivalents ADO/WFC.  
  
## <a name="applies-to"></a>S'applique à  
 [Open, méthode (objet Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)
