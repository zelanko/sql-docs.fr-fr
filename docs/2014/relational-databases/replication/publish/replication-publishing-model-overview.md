---
title: Vue d’ensemble du modèle de publication de réplication
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], publishing model
- subscriptions [SQL Server replication], about subscriptions
- articles [SQL Server replication]
- publications [SQL Server replication]
- Publishers [SQL Server replication], about Publishers
- Subscribers [SQL Server replication]
- Distributors [SQL Server replication], about Distributors
- Subscribers [SQL Server replication], about Subscribers
- articles [SQL Server replication], about articles
- publications [SQL Server replication], about publications
- Distributors [SQL Server replication]
ms.assetid: b9567832-e6a8-45b2-a3ed-ea12aa002f4b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 71c462baf00d4129b4efaea0eb39b3a08e6c7ce6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63261880"
---
# <a name="replication-publishing-model-overview"></a>Vue d’ensemble du modèle de publication de réplication
  La réplication utilise une métaphore de l'industrie de l'édition pour représenter les composants d'une topologie de réplication ; elle comprend un serveur de publication, un serveur de distribution, des abonnés, des publications, des articles et des abonnements. Il est utile de penser [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à la réplication en termes de magazine :  
  
-   L'éditeur d'un magazine produit une ou plusieurs publications  
  
-   Une publication contient des articles  
  
-   L'éditeur distribue le magazine directement ou bien utilise un distributeur  
  
-   Les abonnés reçoivent les publications auxquelles ils se sont abonnés  
  
 Même si la métaphore du magazine est utile à la compréhension de la réplication, il est important de noter que la réplication [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] inclut des fonctionnalités qui ne sont pas représentées dans cette métaphore, en particulier la possibilité pour un Abonné d'effectuer des mises à jour et pour un serveur de publication d'envoyer des modifications incrémentielles aux articles d'une publication.  
  
 Une *topologie de réplication* définit la relation entre les serveurs et les copies des données, et clarifie la logique qui détermine les flux des données entre les serveurs. La copie et le déplacement de données entre le serveur de publication et les Abonnés sont pris en charge par plusieurs processus de réplication (appelés *agents*) : L'illustration suivante donne une vue d'ensemble des composants et des processus impliqués dans la réplication.  
  
 ![Composants et flux de données de réplication](../media/replintro1.gif "Composants et flux de données de réplication")  
  
## <a name="publisher"></a>Serveur de publication  
 Le serveur de publication est une instance de base de données qui rend les données disponibles à d'autres emplacements via la réplication. Le serveur de publication peut avoir une ou plusieurs publications définissant chacune un ensemble d'objets et de données logiquement liés et qui doit être répliqué.  
  
## <a name="distributor"></a>Serveur de distribution  
 Le serveur de distribution est une instance de base de données qui fonctionne comme un magasin pour les données spécifiques de la réplication associées à un ou plusieurs serveurs de publication. Chaque serveur de publication est associé à une seule base de données (appelée base de données de distribution) au niveau du serveur de distribution. La base de données de distribution stocke les données d'état de la réplication, les métadonnées de la publication et, dans certains cas, fonctionne comme une file d'attente pour le déplacement des données du serveur de publication vers les Abonnés. Dans de nombreux cas, un même serveur de base de données fonctionne à la fois comme serveur de publication et comme serveur de distribution. On parle de *serveur de distribution local*. Quand le serveur de publication et le serveur de distribution sont configurés sur des instances de serveur de base de données distinctes, le serveur de distribution est appelé *serveur de distribution distant*.  
  
## <a name="subscribers"></a>Abonnés  
 Un Abonné est une instance de base de données qui reçoit des données répliquées. Un Abonné peut recevoir des données de plusieurs serveurs de publication et de plusieurs publications. En fonction du type de réplication choisi, l'Abonné peut aussi répercuter des modifications auprès du serveur de publication ou rééditer les données vers d'autres Abonnés.  
  
## <a name="article"></a>Article  
 Un article identifie un objet de base de données qui fait partie d'une publication. Une publication peut contenir différents types d'articles : des tables, des vues, des procédures stockées et d'autres objets. Quand des tables sont publiées en tant qu'articles, des filtres peuvent être utilisés pour limiter les colonnes et les lignes de données envoyées aux Abonnés.  
  
## <a name="publication"></a>Publication  
 Une publication est une collection d'un ou plusieurs articles provenant d'une base de données. Le regroupement de plusieurs articles en une publication facilite la spécification d'un ensemble logique d'objets de base de données et de données qui sont répliqués comme une seule unité.  
  
## <a name="subscription"></a>Subscription  
 Un abonnement est une requête portant sur la remise d'une copie d'une publication à un Abonné. L'abonnement définit la publication qui sera reçue, et où et quand elle sera reçue. Il existe deux types d'abonnements : les abonnements par émission de données et les abonnements par extraction. Pour plus d’informations sur les abonnements par envoi et par extraction de données, consultez [S’abonner à des publications](../subscribe-to-publications.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des Agents de réplication](../agents/replication-agents-overview.md)   
 [Types de réplication](../types-of-replication.md)   
 [Configurez la réplication pour groupes de disponibilité AlwaysOn (SQL Server) qui](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) [gère une base de données de publication alwayson &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)  
  
  
