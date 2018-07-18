---
title: Propriétés du serveur de distribution, Général | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distproperties.general.f1
helpviewer_keywords:
- Distributor Properties dialog box
ms.assetid: ab4120ec-e524-4c0c-8b48-f2f40adb1a3b
caps.latest.revision: 21
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d2a32e262bd8096ad77ce0ea813e7ced8440c1dc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37324179"
---
# <a name="distributor-properties-general"></a>Propriétés du serveur de distribution, Général
  La page **Général** de la boîte de dialogue **Propriétés du serveur de distribution** vous permet d'ajouter et de supprimer des bases de données de distribution et d'en définir des propriétés.  
  
 La base de données de distribution stocke les métadonnées et les données d'historique pour tous les types de réplications, et les transactions pour la réplication transactionnelle. Dans de nombreux cas, une seule base de données de distribution est suffisante. Mais si plusieurs serveurs de publication n'utilisent qu'un seul serveur de distribution, étudiez l'éventualité de créer une base de données de distribution propre à chaque serveur de publication. Ainsi, vous vous assurerez que les données transitant entre chaque base de données de distribution seront bien séparées.  
  
## <a name="options"></a>Options  
 **Bases de données**  
 La grille de propriétés **Bases de données** répertorie le nom et les propriétés de rétention des bases de données de distribution se trouvant sur le serveur de distribution. La**rétention des transactions** est la durée pendant laquelle les transactions sont stockées en vue de leur réplication transactionnelle (la rétention des transactions est également connue sous le nom de rétention de distribution). La**rétention des historiques** est la durée pendant laquelle les métadonnées des historiques sont stockées en vue de leur réplication de quelque type que ce soit. Pour plus d’informations sur la rétention de la distribution, consultez [Expiration et désactivation des abonnements](subscription-expiration-and-deactivation.md).  
  
 Cliquez sur le bouton représenté par des points de suspension (**...**) dans la grille des propriétés **Bases de données** pour ouvrir la boîte de dialogue **Propriétés de la base de données de distribution** .  
  
 **Nouveau**  
 Permet de créer une base de données de distribution.  
  
 **Supprimer**  
 Sélectionnez une base de données de distribution dans la grille des propriétés **Bases de données** , puis cliquez sur **Supprimer** pour supprimer la base de données. Vous ne pouvez pas supprimer la base de données de distribution s'il n'existe qu'une seule base de données de ce type. Chaque serveur de distribution doit en effet disposer d'au moins une base de données de distribution. Pour les supprimer toutes, vous devez dans ce cas désactiver la distribution sur l'ordinateur. Pour plus d’informations, consultez [Désactiver la publication et la distribution](disable-publishing-and-distribution.md).  
  
 **Valeurs par défaut du profil**  
 Permet d'accéder aux profils des agents de réplication dans la boîte de dialogue **Profils de l'Agent** . Pour plus d'informations sur ces profils, consultez [Replication Agent Profiles](agents/replication-agent-profiles.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la distribution](configure-distribution.md)   
 [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md)  
  
  
