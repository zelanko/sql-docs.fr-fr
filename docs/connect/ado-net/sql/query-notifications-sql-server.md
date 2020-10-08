---
title: Notifications de requête dans SQL Server
description: Décrit comment les applications .NET peuvent demander une notification à partir de SQL Server lorsque les données sont modifiées.
ms.date: 08/15/2019
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: b5f4500645b60a98dd97166e12bdf0899149b1c4
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91725600"
---
# <a name="query-notifications-in-sql-server"></a>Notifications de requête dans SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Basées sur l’infrastructure de Service Broker, les notifications de requêtes permettent aux applications d’être notifiées en cas de modification des données. Cette fonctionnalité est particulièrement utile pour les applications qui fournissent un cache d'informations à partir d'une base de données, par exemple une application Web, et qui doivent être notifiées en cas de modification des données sources.  
  
Il existe trois façons d’implémenter des notifications de requête à l’aide de ADO.NET :  
  
- L’implémentation de bas niveau est fournie par la classe `SqlNotificationRequest` qui expose les fonctionnalités côté serveur, ce qui vous permet d’exécuter une commande avec une requête de notification.  
  
- L’implémentation de haut niveau est fournie par la classe `SqlDependency`, qui est une classe qui fournit une abstraction de haut niveau de la fonctionnalité de notification entre l’application source et SQL Server, ce qui vous permet d’utiliser une dépendance pour détecter les modifications apportées au serveur. Généralement, il s’agit de la manière la plus simple et la plus efficace, pour des applications clientes managées, d’exploiter les fonctionnalités de notification de SQL Server en utilisant le fournisseur de données Microsoft SqlClient pour SQL Server.  
  
- De plus, les applications web créées avec ASP.NET 2.0 ou ultérieur peuvent utiliser les classes d’assistance `SqlCacheDependency`.  
  
Les notifications de requête sont utilisées pour les applications qui doivent actualiser des affichages ou des caches en réponse aux modifications des données sous-jacentes. Microsoft SQL Server permet aux applications .NET d’envoyer une commande à SQL Server et de demander la génération d’une notification si l’exécution de cette commande produit des ensembles de résultats différents de ceux extraits initialement. Les notifications générées au niveau du serveur sont envoyées par l’intermédiaire de files d’attente pour un traitement ultérieur.  
  
Vous pouvez configurer des notifications pour les instructions SELECT et EXECUTE. Lorsque vous utilisez une instruction EXECUTE, SQL Server enregistre une notification pour la commande exécutée plutôt que l’instruction EXECUTE elle-même. La commande doit satisfaire les exigences et limitations applicables aux instructions SELECT. Quand une commande qui enregistre une notification contient plusieurs instructions, le moteur de base de données crée une notification pour chaque instruction du traitement.  
  
Si vous développez une application où vous avez besoin de notifications à la fraction de seconde fiables quand les données sont modifiées, consultez les sections **Planification d’une stratégie efficace de notifications de requête** et **Alternatives aux notifications de requête** dans la rubrique [Planification des notifications](/previous-versions/sql/sql-server-2008-r2/ms187528(v=sql.105)) de la Documentation en ligne de SQL Server. Pour plus d’informations sur les Notifications de requêtes et SQL Server Service Broker, consultez les liens suivants vers les rubriques dans la Documentation en ligne de SQL Server.  
  
**Documentation SQL Server**  
  
- [Utilisation des notifications de requêtes](/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))  
  
- [Création d’une requête pour notification](/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Développement (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))  
  
- [Centre d’informations du développeur Service Broker](/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Guide du développeur (Service Broker)](/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="in-this-section"></a>Contenu de cette section  
[Activation de notifications de requête](enable-query-notifications.md)  
Explique comment utiliser les notifications de requêtes, notamment les exigences pour les activer et les utiliser.  
  
[SqlDependency dans une application ASP.NET](sqldependency-aspnet-app.md)  
Montre comment utiliser les notifications de requêtes à partir d'une application ASP.NET.  
  
[Détection des changements avec SqlDependency](detect-changes-sqldependency.md)  
Montre comment détecter si les résultats de la requête sont différents de ceux qui ont été reçus à l’origine.  
  
[Exécution de SqlCommand avec une SqlNotificationRequest](sqlcommand-execution-sqlnotificationrequest.md)  
Illustre la configuration d’un objet <xref:Microsoft.Data.SqlClient.SqlCommand> pour utiliser une notification de requête.  
  
## <a name="reference"></a>Informations de référence  
<xref:Microsoft.Data.Sql.SqlNotificationRequest>  
Décrit la classe <xref:Microsoft.Data.Sql.SqlNotificationRequest> et tous ses membres.  
  
<xref:Microsoft.Data.SqlClient.SqlDependency>  
Décrit la classe <xref:Microsoft.Data.SqlClient.SqlDependency> et tous ses membres.  
  
<xref:System.Web.Caching.SqlCacheDependency>  
Décrit la classe <xref:System.Web.Caching.SqlCacheDependency> et tous ses membres.  
  
## <a name="next-steps"></a>Étapes suivantes
- [SQL Server et ADO.NET](index.md)