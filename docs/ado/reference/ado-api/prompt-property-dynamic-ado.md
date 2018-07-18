---
title: Demander propriété dynamique (ADO) | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Prompt property [ADO]
ms.assetid: c4f001b5-8d16-4d39-a42e-c0e2faaaceaf
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a7b5c0637f7befb1419f5cb96bbcd421d59cc7b8
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280629"
---
# <a name="prompt-property-dynamic-ado"></a>Demander propriété dynamique (ADO)
Spécifie si le fournisseur OLE DB doit inviter l’utilisateur pour les informations d’initialisation.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit et renvoie un [ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md) valeur.  
  
## <a name="remarks"></a>Notes  
 **Invite de commandes** est une propriété dynamique, ce qui peut être ajoutée à la [connexion](../../../ado/reference/ado-api/connection-object-ado.md) l’objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection par le fournisseur OLE DB. Pour demander les informations d’initialisation, les fournisseurs OLE DB affiche généralement une boîte de dialogue à l’utilisateur.  
  
 Propriétés dynamiques d’un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet sont perdues lorsque le **connexion** est fermé. Le **invite** propriété doit être réinitialisée avant de rouvrir le **connexion** pour utiliser une valeur autre que la valeur par défaut.  
  
> [!NOTE]
>  Ne spécifiez pas que le fournisseur doit demander à l’utilisateur dans les scénarios dans lesquels l’utilisateur sera pas en mesure de répondre à la boîte de dialogue. Par exemple, l’utilisateur ne sera pas en mesure de répondre si l’application s’exécute sur un système serveur et non sur le client de l’utilisateur, ou si l’application est en cours d’exécution sur un système sans utilisateur connecté. Dans ce cas, l’application attend indéfiniment une réponse et semblera bloquée.  
  
## <a name="usage"></a>Utilisation  
  
```  
Set cn = New Connection  
cn.Provider = "SQLOLEDB"  
cn.Properties("Prompt") = adPromptNever    ' do not prompt the user  
```  
  
## <a name="applies-to"></a>S'applique à  
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)
