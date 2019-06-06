---
title: MarshalOptions, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MarshalOptions
helpviewer_keywords:
- MarshalOptions property [ADO]
ms.assetid: 390c8abf-133e-40da-8b99-8f748a983e4f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 69b9b44fc20fe832bffdd4c03536117a626916ac
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66697293"
---
# <a name="marshaloptions-property-ado"></a>MarshalOptions, propriété (ADO)
Indique les enregistrements de la [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) doivent être marshalées vers le serveur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un [MarshalOptions](../../../ado/reference/ado-api/marshaloptionsenum.md) valeur. La valeur par défaut est **adMarshalAll**.  
  
## <a name="remarks"></a>Notes  
 Lors de l’utilisation d’une côté client [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), enregistrements qui ont été modifiés sur le client mis à jour dans la couche intermédiaire ou un serveur Web via une technique appelée marshaling, le processus d’empaquetage et la méthode d’interface d’envoi paramètres au-delà des limites de thread ou processus. Définition de la **MarshalOptions** propriété peut améliorer les performances lors du marshaling des données distantes modifiées pour la mise à jour au niveau intermédiaire ou au serveur Web.  
  
> [!NOTE]
>  **Utilisation de Service de données à distance** cette propriété est utilisée uniquement sur une côté client **Recordset**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [MarshalOptions, propriété-Exemple (VB)](../../../ado/reference/ado-api/marshaloptions-property-example-vb.md)   
 [MarshalOptions, exemple de propriété (VC++)](../../../ado/reference/ado-api/marshaloptions-property-example-vc.md)   
