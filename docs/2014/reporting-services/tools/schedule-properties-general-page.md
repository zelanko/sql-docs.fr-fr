---
title: Propriétés de planification (page Général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.general.f1
ms.assetid: 20e43966-6caf-4972-a2e2-0d9131ac8f51
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 98d013126fe1db1b8101d5ae451f658546f6d1f9
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66099737"
---
# <a name="schedule-properties-general-page"></a>Propriétés de planification (page Général)
  Utilisez cette page pour afficher ou modifier une planification partagée. Les planifications partagées peuvent être utilisées à la place des planifications spécifiques des rapports ou spécifiques des abonnements. Les modifications apportées à la planification sont appliquées après l'avoir enregistrée. La modification d'une planification n'a aucun effet sur les travaux qui sont actuellement en cours. Si vous modifiez une planification pendant qu'elle est utilisée, tous les rapports et abonnements en cours de traitement déclenchés par cette planification pourront être menés à bien.  
  
 Toutes les combinaisons de fréquence ne peuvent pas être prises en charge dans une seule planification. Par exemple, si vous souhaitez exécuter un rapport à 12:00 et 16:00 ous les vendredis, vous devez créer deux planifications quotidiennes qui spécifient le vendredi comme jour d'exécution mais avec une heure de début de 12:00 pour l'une et une heure de début de 16:00 pour la seconde.  
  
 Le traitement de la planification est basé sur l'heure locale du serveur de rapports qui héberge et traite la planification.  
  
 Pour ouvrir cette page, démarrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à un serveur de rapports, ouvrez le dossier **Planifications partagées** , cliquez avec le bouton droit sur une planification partagée, puis sélectionnez **Propriétés**.  
  
> [!NOTE]  
>  Cette fonctionnalité est disponible dans chaque édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et cette page n'apparaît pas lorsque vous exécutez une édition qui n'a pas cette fonctionnalité. Pour obtenir la liste des fonctionnalités prises en charge par les éditions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de, consultez [fonctionnalités prises en charge par les éditions de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).  
  
## <a name="options"></a>Options  
 **Nom**  
 Indique le nom de la planification partagée.  
  
 **Commencer l'exécution de cette planification le**  
 Spécifie la date de début de cette planification.  
  
 **Arrêter cette planification le**  
 Spécifie la date d'expiration de cette planification.  
  
 **Type**  
 Spécifie si la périodicité est basée essentiellement sur les heures, jours, semaines, mois, ou si elle n'est définie qu'une seule fois.  
  
 **Heure (Modèle de récurrence)**  
 Spécifie les options d'exécution d'une opération planifiée par intervalles d'une heure (par exemple, pour exécuter un rapport toutes les 6 heures). Vous pouvez préciser l'intervalle en heures et en minutes.  
  
 **Jour (Modèle de récurrence)**  
 Spécifie les options d'exécution d'une opération planifiée par intervalles d'un jour (par exemple, pour exécuter un rapport tous les 2 jours). Vous pouvez spécifier l'intervalle en jours et à l'heure à laquelle vous voulez exécuter la planification.  
  
 **Semaine (Modèle de récurrence)**  
 Spécifie les options d'exécution d'une opération planifiée par intervalles d'une semaine ou lorsque la périodicité à répéter est en semaines (par exemple, pour exécuter un rapport une semaine sur deux). Vous pouvez spécifier une planification hebdomadaire au jour et à l'heure où vous voulez l'exécuter.  
  
 **Mois (Modèle de récurrence)**  
 Spécifie les options d'exécution d'une opération planifiée par intervalles d'un mois ou lorsque la périodicité à répéter est en mois. Vous pouvez spécifier une planification mensuelle au jour et à l'heure où vous voulez l'exécuter. Vous pouvez ignorer certains mois dans la planification.  
  
 **Toutes**  
 Spécifie une planification exécutée une fois seulement, à une date et une heure spécifiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Serveur de rapports dans Management Studio aide (F1)](report-server-in-management-studio-f1-help.md)   
 [Se connecter à un serveur de rapports dans Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md)   
 [Planifications](../subscriptions/schedules.md)  
  
  
