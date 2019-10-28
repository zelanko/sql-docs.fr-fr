---
title: Exécution de SqlCommand avec une SqlNotificationRequest
description: Illustre la configuration d’un objet SqlCommand pour travailler avec une notification de requête.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 892f11e2d81e3a0733a1f0747c0b72c72ebc79fc
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451947"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a>Exécution de SqlCommand avec une SqlNotificationRequest

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Un <xref:Microsoft.Data.SqlClient.SqlCommand> peut être configuré pour générer une notification lorsque les données sont modifiées après avoir été extraites du serveur et que le jeu de résultats est différent si la requête a été exécutée à nouveau. Cela est utile dans les scénarios où vous souhaitez utiliser des files d’attente de notification personnalisées sur le serveur ou lorsque vous ne souhaitez pas conserver les objets actifs.

## <a name="creating-the-notification-request"></a>Création de la demande de notification

Vous pouvez utiliser un objet <xref:Microsoft.Data.Sql.SqlNotificationRequest> pour créer la demande de notification en le liant à un objet `SqlCommand`. Une fois la requête créée, vous n’avez plus besoin de l’objet `SqlNotificationRequest`. Vous pouvez interroger la file d’attente pour toutes les notifications et y répondre de manière appropriée. Des notifications peuvent se produire même si l’application est arrêtée et redémarrée par la suite.

Quand la commande avec la notification associée est exécutée, toute modification du jeu de résultats déclenche l’envoi d’un message à la file d’attente SQL Server qui a été configurée dans la demande de notification.

La manière dont vous interrogez la file d’attente SQL Server et interprétez le message est propre à votre application. L’application est responsable de l’interrogation de la file d’attente et de la réaction en fonction du contenu du message.

> [!NOTE]
> Lors de l’utilisation de SQL Server demandes de notification avec <xref:Microsoft.Data.SqlClient.SqlDependency>, créez votre propre nom de file d’attente au lieu d’utiliser le nom du service par défaut.

Il n’existe aucun nouvel élément de sécurité côté client pour <xref:Microsoft.Data.Sql.SqlNotificationRequest>. Il s’agit principalement d’une fonctionnalité de serveur, et le serveur a créé des privilèges spéciaux dont les utilisateurs doivent disposer pour demander une notification.

### <a name="example"></a>Exemple

Le fragment de code suivant montre comment créer un <xref:Microsoft.Data.Sql.SqlNotificationRequest> et l’associer à un <xref:Microsoft.Data.SqlClient.SqlCommand>.

```csharp
// Assume connection is an open SqlConnection.
// Create a new SqlCommand object.
SqlCommand command=new SqlCommand(
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);

// Create a SqlNotificationRequest object.
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="next-steps"></a>Étapes suivantes
- [Notifications de requête dans SQL Server](query-notifications-sql-server.md)
