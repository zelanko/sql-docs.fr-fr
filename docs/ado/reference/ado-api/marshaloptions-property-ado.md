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
author: rothja
ms.author: jroth
ms.openlocfilehash: 182946d30141ecbbcc2cba706338609b431abb97
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2020
ms.locfileid: "82754495"
---
# <a name="marshaloptions-property-ado"></a>MarshalOptions, propriété (ADO)
Indique les enregistrements du [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) qui doivent être remarshalés sur le serveur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur [MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md) . La valeur par défaut est **adMarshalAll**.  
  
## <a name="remarks"></a>Notes  
 Lors de l’utilisation d’un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)côté client, les enregistrements qui ont été modifiés sur le client sont réécrits sur la couche intermédiaire ou le serveur Web via une technique appelée marshaling, processus d’empaquetage et d’envoi de paramètres de méthode d’interface à travers les limites de thread ou de processus. La définition de la propriété **MarshalOptions** peut améliorer les performances lorsque les données distantes modifiées sont marshalées pour être mises à jour vers la couche intermédiaire ou le serveur Web.  
  
> [!NOTE]
>  **Utilisation des services de données distants** Cette propriété est utilisée uniquement sur un **jeu d’enregistrements**côté client.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [MarshalOptions, exemple de propriété (VB)](../../../ado/reference/ado-api/marshaloptions-property-example-vb.md)   
 [MarshalOptions, exemple de propriété (VC++)](../../../ado/reference/ado-api/marshaloptions-property-example-vc.md)   
