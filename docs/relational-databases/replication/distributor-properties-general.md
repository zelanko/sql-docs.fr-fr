---
title: "Propri&#233;t&#233;s du serveur de distribution, page G&#233;n&#233;ral | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.configdistwizard.distproperties.general.f1"
helpviewer_keywords: 
  - "boîte de dialogue Propriétés du serveur de distribution"
ms.assetid: ab4120ec-e524-4c0c-8b48-f2f40adb1a3b
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Propri&#233;t&#233;s du serveur de distribution, page G&#233;n&#233;ral
  La page **Général** de la boîte de dialogue **Propriétés du serveur de distribution** vous permet d'ajouter et de supprimer des bases de données de distribution et d'en définir des propriétés.  
  
 La base de données de distribution stocke les métadonnées et les données d'historique pour tous les types de réplications, et les transactions pour la réplication transactionnelle. Dans de nombreux cas, une seule base de données de distribution est suffisante. Mais si plusieurs serveurs de publication n'utilisent qu'un seul serveur de distribution, étudiez l'éventualité de créer une base de données de distribution propre à chaque serveur de publication. Ainsi, vous vous assurerez que les données transitant entre chaque base de données de distribution seront bien séparées.  
  
## Options  
 **Bases de données**  
 Le **bases de données** grille des propriétés affiche les propriétés de nom et de rétention des bases de données de distribution sur le serveur de distribution. **Rétention des transactions** est la durée pendant laquelle les transactions sont stockées pour la réplication transactionnelle (rétention des transactions est également appelé durée de rétention de distribution). La**rétention des historiques** est la durée pendant laquelle les métadonnées des historiques sont stockées en vue de leur réplication de quelque type que ce soit. Pour plus d’informations sur la rétention de distribution, consultez [Expiration de l’abonnement et de désactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 Cliquez sur le bouton des propriétés (**...**) dans le **bases de données** grille des propriétés pour lancer le **Propriétés de base de données de Distribution** boîte de dialogue.  
  
 **Nouveau**  
 Permet de créer une base de données de distribution.  
  
 **Delete**  
 Sélectionnez une base de données de distribution existant dans la **bases de données** grille des propriétés, puis cliquez sur **Supprimer** pour supprimer la base de données. Vous ne pouvez pas supprimer la base de données de distribution s'il n'existe qu'une seule base de données de ce type. Chaque serveur de distribution doit en effet disposer d'au moins une base de données de distribution. Pour les supprimer toutes, vous devez dans ce cas désactiver la distribution sur l'ordinateur. Pour plus d’informations, consultez [désactiver la publication et Distribution](../../relational-databases/replication/disable-publishing-and-distribution.md).  
  
 **Valeurs par défaut du profil**  
 Cliquez pour des profils d’agent de réplication d’accès dans la **profils d’Agent** boîte de dialogue. Pour plus d'informations sur ces profils, consultez [Replication Agent Profiles](../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
## Voir aussi  
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  