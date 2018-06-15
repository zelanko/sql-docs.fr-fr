---
title: ConnectionTimeout, propriété (ADO) | Documents Microsoft
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
f1_keywords:
- Connection15::ConnectionTimeout
helpviewer_keywords:
- ConnectionTimeout property [ADO]
ms.assetid: 8904a403-1383-4b4b-b53d-5c01d6f5deac
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a1f90890b8f48a4a00fe9469ed978d42d3f6a86a
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35277008"
---
# <a name="connectiontimeout-property-ado"></a>ConnectionTimeout, propriété (ADO)
Indique le délai d’attente lors de l’établissement d’une connexion avant d’abandonner la tentative et de générer une erreur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **Long** valeur qui indique, en secondes, la durée d’attente pour la connexion à ouvrir. Valeur par défaut est 15.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **ConnectionTimeout** propriété sur un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) si retards dus au réseau du trafic ou serveur une utilisation intensive rendent nécessaire d’abandonner une tentative de connexion de l’objet. Si l’heure à partir de la **ConnectionTimeout** paramètre de la propriété s’écoule avant l’ouverture de la connexion, une erreur se produit et ADO annule la tentative. Si vous définissez la propriété sur zéro, ADO attend indéfiniment que la connexion est ouverte. Assurez-vous que le fournisseur auquel vous écrivez du code prend en charge la **ConnectionTimeout** fonctionnalité.  
  
 Le **ConnectionTimeout** propriété est en lecture/écriture lorsque la connexion est fermée et en lecture seule lorsqu’il est ouvert.  
  
## <a name="applies-to"></a>S'applique à  
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ConnectionString, ConnectionTimeout et propriétés de l’état d’exemple (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString, ConnectionTimeout et l’état d’exemple (VC ++)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
 [CommandTimeout, propriété (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)
