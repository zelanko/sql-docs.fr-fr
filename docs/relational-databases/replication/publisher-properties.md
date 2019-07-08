---
title: Réplication SQL Server, boîte de dialogue Propriétés du serveur de publication | Microsoft Docs
ms.custom: ''
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configdistwizard.distpubproperties.f1
- sql13.rep.configdistwizard.pubproperties.general.f1
- sql13.rep.configdistwizard.pubproperties.pubdb.f1
- sql13.rep.configdistwizard.pubproperties.subscribers.f1
ms.assetid: 98df1aea-0406-40bf-a917-4bd80464125c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: def9df7e03f596cf519eebebd7b2ca83a912fe98
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67580019"
---
# <a name="sql-server-replication-publisher-properties-dialog-box"></a>Réplication SQL Server, boîte de dialogue Propriétés du serveur de publication
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette rubrique décrit les différentes options disponibles dans la boîte de dialogue Propriétés du serveur de publication. 

## <a name="general"></a>Général
  La page **Général** de la boîte de dialogue **Propriétés du serveur de publication** contient des informations en lecture seule sur le serveur de distribution et la base de données de distribution qu'utilise le serveur de publication. Pour changer le serveur de distribution ou la base de données de distribution d'un serveur de publication :  
  
1.  Désactivez la publication sur le serveur de publication. Pour plus d’informations, consultez [Désactiver la publication et la distribution](../../relational-databases/replication/disable-publishing-and-distribution.md).    
2.  Reconfigurez la publication et la distribution. Pour plus d’informations, consultez [Configure Publishing and Distribution](../../relational-databases/replication/configure-publishing-and-distribution.md).  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="distributor"></a>Serveur de distribution 
La boîte de dialogue **Propriétés du serveur de publication** permet d'afficher et de modifier les propriétés associées à la relation existant entre le serveur de publication et son serveur de distribution.  
  
### <a name="options"></a>Options  
 **Connexion de l'agent au serveur de publication**  
 Permet d'ajouter le contexte selon lequel les agents suivants établissent les connexions du serveur de distribution au serveur de publication :  
  
-   l'Agent de lecture de la file d'attente propre aux publications transactionnelles autorisant les abonnements de mise à jour dans la file d'attente ;    
-   l'Agent d'instantané et l'Agent de lecture du journal pour les publications Oracle.  
  
 Choisissez l'option **Imiter le compte de processus de l'Agent** afin d'établir des connexions au serveur de publication grâce au contexte du compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows fourni et sous lequel ces agents doivent s'exécuter, ou bien choisissez **Authentification SQL Server**et saisissez alors une valeur pour chacun des champs **Connexion** et **Mot de passe**. Nous vous recommandons de sélectionner plutôt l'option **Imiter le compte de processus de l'Agent**. Pour plus d’informations sur la sécurité de l’agent, consultez [Modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
 Les comptes Windows sous lesquels ces agents s'exécutent sont précisés dans l'Assistant Nouvelle publication. Ces comptes peuvent être modifiés de l'une des façons suivantes :  
  
-   dans la boîte de dialogue **Propriétés du serveur de distribution** , en ce qui concerne l'Agent de lecture de la file d'attente ;    
-   dans la boîte de dialogue **Propriétés du serveur de publication** , dans le cas de l'Agent d'instantané et de l'Agent de lecture du journal.  
  
 **Divers**  
 Les propriétés **Type de serveur de publication** et **Nom de la base de données de distribution** sont des propriétés en lecture seule. La propriété **Dossier d'instantanés par défaut** est cependant modifiable. Pour plus d’informations sur le dossier d’instantanés, consultez [Sécuriser le dossier d’instantanés](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  

## <a name="publication-databases"></a>Bases de données de publication
  La page **Bases de données de publication** de la boîte de dialogue **Propriétés du serveur de publication** permet à un utilisateur dans le rôle serveur fixe **sysadmin** d'autoriser la réplication des bases de données. L'activation d'une base de données ne publie pas la base de données ; elle permet à un utilisateur du rôle fixe de base de données **db_owner** de créer des publications dans la base de données.  
  
## <a name="options"></a>Options  
 **Transactionnelle**  
 Activez cette case à cocher pour permettre aux utilisateurs du rôle de base de données fixe **db_owner** de créer des publications d'instantanés ou des publications transactionnelles dans la base de données. 
  
 **Fusion**  
 Activez cette case à cocher pour permettre aux utilisateurs du rôle de base de données fixe **db_owner** de créer des publications de fusion dans la base de données.  
  

## <a name="subcribers"></a>Abonnés
  La page **Abonnés** de la boîte de dialogue **Propriétés du serveur de publication** est utilisée pour les serveurs de publication qui exécutent les versions de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Cette page permet d'indiquer que les abonnés peuvent recevoir des données des publications de ce serveur de publication. La possibilité pour un abonné de recevoir des données du serveur de publication ne crée pas d'abonnements aux publications sur le serveur de publication. Pour créer un abonnement, vous devez utiliser l'Assistant Nouvel abonnement.  
  
### <a name="options"></a>Options  
 **Abonnés**  
 La grille de propriétés **Abonnés** indique les abonnés qui peuvent recevoir des données de publication du serveur de publication. Cliquez sur le bouton des propriétés ( **...** ) à côté d'un abonné pour afficher et définir des propriétés supplémentaires.  
  
 **Ajouter**  
 Cliquez sur **Ajouter** pour ajouter un abonné, puis cliquez sur **Ajout un Abonné SQL Server** ou **Ajouter un Abonné non-SQL Server**.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Créer une publication](../../relational-databases/replication/publish/create-a-publication.md)   


  
