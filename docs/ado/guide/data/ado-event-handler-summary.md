---
title: Résumé du Gestionnaire d’événements ADO | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO], about event handlers
- event handlers [ADO]
ms.assetid: b34f4472-5e04-4a2c-ab64-38d6eca31a69
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 93790b3df8cb1d78ab2e0988cdc43cbd9af0718c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63063015"
---
# <a name="ado-connection-and-recordset-events"></a>Connexion ADO et événements de jeu d’enregistrements
Deux objets ADO peuvent déclencher des événements : le [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet et le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet. Le **ConnectionEvent** famille se rapporte aux opérations sur le **connexion** objet et le **RecordsetEvent** famille se rapporte aux opérations sur le  **Jeu d’enregistrements** objet.

-   **Événements de connexion**: Événements émis quand une transaction sur une connexion commence, est validée ou est restaurée ; Lorsqu’un [commande](../../../ado/reference/ado-api/command-object-ado.md) exécute ; lorsqu’un avertissement se produit pendant une **l’événement de connexion** opération ; ou quand un **connexion** commence ou se termine.

-   **Événements de jeu d’enregistrements**: Événements sont émis autour des opérations d’extraction asynchrones, ainsi que lorsque vous naviguez dans les lignes d’un **Recordset** d’objet, de modifier un champ dans une ligne d’un **Recordset**, modifiez une ligne dans un  **Jeu d’enregistrements**, ouvrez un **Recordset** avec un curseur côté serveur, vous devez fermer un **Recordset**, ou assurez-vous que le modifiez dans le **Recordset**.

 Les tableaux suivants récapitulent les événements et leurs descriptions.

|ConnectionEvent|Description|
|---------------------|-----------------|
|[BeginTransComplete, CommitTransComplete, RollbackTransComplete](../../../ado/reference/ado-api/begintranscomplete-committranscomplete-and-rollbacktranscomplete-events-ado.md)|**Gestion des transactions** -notification indiquant que la transaction en cours sur la connexion a démarré, validée ou restaurée.|
|[WillConnect](../../../ado/reference/ado-api/willconnect-event-ado.md), [ConnectComplete, Disconnect](../../../ado/reference/ado-api/connectcomplete-and-disconnect-events-ado.md)|**Gestion des connexions** -Notification qui démarre la connexion actuelle, a démarré ou s’est terminée.|
|[WillExecute](../../../ado/reference/ado-api/willexecute-event-ado.md), [ExecuteComplete](../../../ado/reference/ado-api/executecomplete-event-ado.md)|**Gestion de l’exécution de la commande** -notification indiquant que l’exécution de la commande en cours sur la connexion démarre ou s’est terminée.|
|[InfoMessage](../../../ado/reference/ado-api/infomessage-event-ado.md)|**D’information** -Notification qu’il existe des informations supplémentaires sur l’opération en cours.|

|RecordsetEvent|Description|
|--------------------|-----------------|
|[FetchProgress](../../../ado/reference/ado-api/fetchprogress-event-ado.md), [FetchComplete](../../../ado/reference/ado-api/fetchcomplete-event-ado.md)|**État de récupération** -Notification de la progression d’une opération de récupération de données, ou que l’opération de récupération est terminée. Ces événements sont disponibles uniquement si la **Recordset** a été ouvert à l’aide d’un curseur côté client.|
|[WillChangeField, FieldChangeComplete](../../../ado/reference/ado-api/willchangefield-and-fieldchangecomplete-events-ado.md)|**Gestion des modifications de champ** -notification indiquant que la valeur du champ actuel va changer ou a changé.|
|[WillMove, MoveComplete](../../../ado/reference/ado-api/willmove-and-movecomplete-events-ado.md), [EndOfRecordset](../../../ado/reference/ado-api/endofrecordset-event-ado.md)|**Gestion de la navigation** -Notification cette position de la ligne actuelle dans un **Recordset** changera, a changé ou a atteint la fin de la **Recordset**.|
|[WillChangeRecord, RecordChangeComplete](../../../ado/reference/ado-api/willchangerecord-and-recordchangecomplete-events-ado.md)|**Gestion du changement de ligne** -Notification que quelque chose dans la ligne actuelle de la **Recordset** va changer ou a changé.|
|[WillChangeRecordset, RecordsetChangeComplete](../../../ado/reference/ado-api/willchangerecordset-and-recordsetchangecomplete-events-ado.md)|**Gestion du changement Recordset** -Notification que quelque chose dans le courant **Recordset** va changer ou a changé.|

## <a name="see-also"></a>Voir aussi
 [Instanciation des événements ADO par langage](../../../ado/guide/data/ado-event-instantiation-by-language.md) [événements ADO](../../../ado/reference/ado-api/ado-events.md) [paramètres d’événement](../../../ado/guide/data/event-parameters.md) [fonctionnement conjoint des gestionnaires d’événements](../../../ado/guide/data/how-event-handlers-work-together.md) [Types d’événements](../../../ado/guide/data/types-of-events.md)
