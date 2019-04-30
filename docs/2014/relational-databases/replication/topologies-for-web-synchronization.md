---
title: Topologies pour la synchronisation web | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web synchronization, topologies
- IIS server configuration [SQL Server replication]
ms.assetid: 59444faf-bcb6-4421-a3df-8715753e453b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 62fd4cd78beaeff479fc7cc9ec3abbd79e227e04
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63273549"
---
# <a name="topologies-for-web-synchronization"></a>Topologies pour la synchronisation web
  Vous pouvez choisir parmi différentes topologies de réplication de synchronisation Web [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les façons courantes de configurer une synchronisation Web sont les suivantes :  
  
-   Serveur unique  
  
-   Deux serveurs  
  
-   Plusieurs systèmes [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) et la republication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Pour plus d’informations sur la configuration de la synchronisation web, consultez [Configurer la synchronisation web](configure-web-synchronization.md).  
  
## <a name="single-server"></a>Serveur unique  
 Dans la topologie la plus simple, IIS, le serveur de publication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le serveur de distribution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] résident tous trois sur le même serveur. Les Abonnés se synchronisent en se connectant à IIS sur le serveur de publication. Le serveur de publication peut être situé derrière un pare-feu.  
  
> [!NOTE]  
>  Cette configuration est recommandée uniquement pour les scénarios intranet. Pour les autres scénarios, il est recommandé que le serveur IIS et les serveurs de publication et de distribution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] soient placés sur des ordinateurs distincts.  
  
 ![Synchronisation web avec un serveur unique](media/web-sync02.gif "Synchronisation web avec un serveur unique")  
  
## <a name="two-servers"></a>Deux serveurs  
 Vous pouvez placer IIS sur un serveur et configurer les serveurs de publication et de distribution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur un autre serveur. Le serveur exécutant IIS peut être isolé d'Internet par un pare-feu. Les Abonnés se synchronisent en se connectant à IIS.  
  
 ![Synchronisation web avec deux serveurs](media/web-sync03.gif "Synchronisation web avec deux serveurs")  
  
## <a name="multiple-iis-systems-and-sql-server-republishing"></a>Plusieurs systèmes IIS et la republication SQL Server  
 Si vous devez prendre en charge un très grand nombre d'Abonnés qui se synchronisent au même moment, vous pouvez partitionner le travail entre plusieurs ordinateurs exécutant IIS.  
  
 ![Synchronisation web avec deux serveurs](media/web-sync04.gif "Synchronisation web avec deux serveurs")  
  
 Si un équilibrage de charge est encore nécessaire sur l'ordinateur exécutant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez créer une hiérarchie de republication sur plusieurs ordinateurs. Le serveur de publication de niveau supérieur publie les données vers les Abonnés, qui à leur tour republient ces données, équilibrant la charge des requêtes en provenance des Abonnés.  
  
> [!NOTE]  
>  Les Abonnés ne peuvent effectuer des synchronisations qu'avec un serveur de publication donné. Par exemple, un Abonné au serveur de republication A ne peut effectuer aucune synchronisation avec le serveur de republication B si le serveur A n'est pas disponible.  
  
 ![Synchronisation web avec republication](media/web-sync05.gif "Synchronisation web avec republication")  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la synchronisation web](configure-web-synchronization.md)   
 [Synchronisation web pour la réplication de fusion](web-synchronization-for-merge-replication.md)  
  
  
