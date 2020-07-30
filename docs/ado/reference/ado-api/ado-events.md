---
title: Événements ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO]
- ADO, events
ms.assetid: 0ded5ad9-8f83-4224-95af-38512783b972
author: rothja
ms.author: jroth
ms.openlocfilehash: a93353be1737b38e7acb557a682e84cbb947c2a1
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242869"
---
# <a name="ado-events"></a>Événements ADO

|Événement|Description|  
|-|-|  
|[BeginTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Appelé après l’opération **BeginTrans** .|  
|[CommitTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Appelé après l’opération **CommitTrans** .|  
|[ConnectComplete](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Appelée après le démarrage d’une connexion.|  
|[Déconnexion](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|Appelé après la fin d’une connexion.|  
|[EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|Appelé en cas de tentative de déplacement vers une ligne située au-delà de la fin du **Recordset**.|  
|[ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|Appelé après la fin de l’exécution d’une commande.|  
|[FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|Appelée une fois que tous les enregistrements d’une longue opération asynchrone ont été récupérés dans le **Recordset**.|  
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md)|Appelée régulièrement au cours d’une opération asynchrone de longue durée pour signaler le nombre de lignes qui ont été récupérées actuellement dans le **Recordset**.|  
|[FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Appelé après la modification de la valeur d’un ou plusieurs objets **Field** .|  
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|Appelé chaque fois qu’un avertissement se produit pendant une opération **ConnectionEvent** .|  
|[MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|Appelé après la modification de la position actuelle dans l’ensemble **d’enregistrements** .|  
|[RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Appelé après la modification d’un ou de plusieurs enregistrements.|  
|[RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Appelé après la modification du **Recordset** .|  
|[RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|Appelé après l’opération **RollbackTrans** .|  
|[WillChangeField](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|Appelé avant qu’une opération en attente modifie la valeur d’un ou plusieurs objets **Field** dans le **Recordset**.|  
|[WillChangeRecord](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|Appelé avant qu’un ou plusieurs enregistrements (lignes) du **Recordset** soient modifiés.|  
|[WillChangeRecordset](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|Appelé avant qu’une opération en attente modifie le **Recordset**.|  
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md)|Appelé avant le démarrage d’une connexion.|  
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md)|Appelé juste avant qu’une commande en attente ne s’exécute sur cette connexion et donne à l’utilisateur la possibilité d’examiner et de modifier les paramètres d’exécution en attente.|  
|[WillMove](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md)|L’événement **WillMove** est appelé *avant qu'* une opération en attente modifie la position actuelle dans l’ensemble **d’enregistrements**.|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API ADO](../../../ado/reference/ado-api/ado-api-reference.md)   
 [Collections ADO](../../../ado/reference/ado-api/ado-collections.md)   
 [Propriétés dynamiques ADO](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [Constantes énumérées ADO](../../../ado/reference/ado-api/ado-enumerated-constants.md)   
 [Annexe B : erreurs ADO](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [Gestion des événements ADO](../../../ado/guide/data/handling-ado-events.md)   
 [Méthodes ADO](../../../ado/reference/ado-api/ado-methods.md)   
 [Modèle objet ADO](../../../ado/reference/ado-api/ado-object-model.md)   
 [Objets et interfaces ADO](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [Propriétés ADO](../../../ado/reference/ado-api/ado-properties.md)
