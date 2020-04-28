---
title: Mode, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Mode
- _Stream::Mode
- _Record::Mode
helpviewer_keywords:
- Mode property [ADO]
ms.assetid: 808661eb-0d7c-4e6d-8e40-9dc3bef3d77a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bc5b2e2bce410309656bad5591a3df90781cc8bc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932227"
---
# <a name="mode-property-ado"></a>Mode, propriété (ADO)
Indique les autorisations disponibles pour la modification des données dans une [connexion](../../../ado/reference/ado-api/connection-object-ado.md), un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md)ou un objet de [flux](../../../ado/reference/ado-api/stream-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) . La valeur par défaut d’une **connexion** est **adModeUnknown**. La valeur par défaut d’un objet **Record** est **adModeRead**. La valeur par défaut d’un **flux** associé à une source sous-jacente (ouverte avec une URL comme source, ou en tant que **flux** par défaut d’un **enregistrement**) est **adModeRead**. La valeur par défaut d’un **flux** non associé à une source sous-jacente (instanciée en mémoire) est **adModeUnknown**.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **mode** pour définir ou retourner les autorisations d’accès utilisées par le fournisseur sur la connexion actuelle. Vous pouvez définir la propriété **mode** uniquement lorsque l’objet de **connexion** est fermé.  
  
 Pour un objet de **flux** , si le mode d’accès n’est pas spécifié, il est hérité de la source utilisée pour ouvrir l’objet de **flux** . Par exemple, si un **flux** est ouvert à partir d’un objet **Record** , par défaut, il est ouvert dans le même mode que l' **enregistrement**.  
  
 Cette propriété est en lecture/écriture lorsque l’objet est fermé et en lecture seule pendant que l’objet est ouvert.  
  
> [!NOTE]
>  **Utilisation des services de données distants** Lorsqu’elle est utilisée sur un objet de **connexion** côté client, la propriété **mode** peut uniquement être définie sur **adModeUnknown**.  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Connection, objet (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [IsolationLevel et mode, exemple de propriétés (VB)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vb.md)   
 [IsolationLevel et mode, exemple de propriétés (VC + +)](../../../ado/reference/ado-api/isolationlevel-and-mode-properties-example-vc.md)   
