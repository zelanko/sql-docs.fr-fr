---
title: Prompt, propriété dynamique (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Prompt property [ADO]
ms.assetid: c4f001b5-8d16-4d39-a42e-c0e2faaaceaf
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4f2c778a6e922477cd8b21251a638d430ce15480
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66703157"
---
# <a name="prompt-property-dynamic-ado"></a>Prompt, propriété dynamique (ADO)
Spécifie si le fournisseur OLE DB doit inviter l’utilisateur pour les informations d’initialisation.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit et renvoie un [ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md) valeur.  
  
## <a name="remarks"></a>Notes  
 **Invite** est une propriété dynamique, qui peut être ajoutée à la [connexion](../../../ado/reference/ado-api/connection-object-ado.md) l’objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection par le fournisseur OLE DB. Pour demander les informations d’initialisation, les fournisseurs OLE DB affiche généralement une boîte de dialogue à l’utilisateur.  
  
 Propriétés dynamiques d’un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet sont perdues lorsque le **connexion** est fermé. Le **invite** propriété doit être réinitialisée avant de rouvrir le **connexion** pour utiliser une valeur autre que la valeur par défaut.  
  
> [!NOTE]
>  Ne spécifiez pas que le fournisseur doit inviter l’utilisateur dans les scénarios dans lesquels l’utilisateur sera pas en mesure de répondre à la boîte de dialogue. Par exemple, l’utilisateur ne sera pas en mesure de répondre si l’application s’exécute sur un système de serveur au lieu de sur le client de l’utilisateur, ou si l’application s’exécute sur un système sans utilisateur connecté. Dans ce cas, l’application attend indéfiniment une réponse et semblera bloquée.  
  
## <a name="usage"></a>Utilisation  
  
```  
Set cn = New Connection  
cn.Provider = "SQLOLEDB"  
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user  
```  
  
## <a name="applies-to"></a>S'applique à  
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)
