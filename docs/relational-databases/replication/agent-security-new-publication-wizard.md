---
title: "S&#233;curit&#233; de l&#39;agent (Assistant Nouvelle publication) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.agentsecurity.articles.f1"
ms.assetid: 05ae44df-8e9f-46ea-95f6-972ad109c6c0
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# S&#233;curit&#233; de l&#39;agent (Assistant Nouvelle publication)
  Le **sécurité de l’Agent** page vous permet de spécifier les comptes sous lequel les agents suivants s’exécutent et établissent des connexions aux ordinateurs dans une topologie de réplication :  
  
-   Agent d'instantané pour toutes les publications ;  
  
-   Agent de lecture du journal pour toutes les publications transactionnelles ;  
  
-   Agent de lecture de la file d'attente pour les publications transactionnelles qui autorisent les abonnements pouvant être mis à jour. Le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] travail de l’Agent pour cet agent est créé si vous avez spécifié **publication transactionnelle avec abonnements actualisables** sur la **Type de Publication** page, quel que soit le type d’à abonnements que vous utilisez. Pour plus d'informations sur les abonnements pouvant être mis à jour, consultez [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
 Pour plus d’informations sur les autorisations requises par les agents et les meilleures pratiques pour la sécurité de la réplication, consultez [modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md) et [meilleures pratiques de sécurité de réplication](../../relational-databases/replication/security/replication-security-best-practices.md).  
  
## Options  
 **Agent d'instantané**  
 Affiché pour toutes les publications. Cliquez sur **les paramètres de sécurité** pour spécifier les paramètres de sécurité dans le **sécurité de l’Agent de capture instantanée** boîte de dialogue.  
  
 Cliquez sur **aide** sur la **sécurité de l’Agent de capture instantanée** boîte de dialogue pour plus d’informations sur les autorisations requises pour les comptes utilisés par l’Agent de capture instantanée.  
  
 **l'Agent de lecture du journal ;**  
 Affiché pour toutes les publications transactionnelles. Cliquez sur **les paramètres de sécurité** pour spécifier les paramètres de sécurité dans le **sécurité de l’Agent de lecture du journal** boîte de dialogue.  
  
 Cliquez sur **aide** sur la **sécurité de l’Agent de lecture du journal** boîte de dialogue pour plus d’informations sur les autorisations requises pour les comptes utilisés par l’Agent de lecture du journal.  
  
> [!NOTE]  
>  Il existe un Agent de lecture du journal pour chaque base de données publiée utilisant la réplication transactionnelle. Si une publication transactionnelle existe déjà dans la base de données, les paramètres de sécurité sont en lecture seule. Vous pouvez modifier les paramètres dans le **Propriétés de la Publication** boîte de dialogue, mais les modifications apportées affectent toutes les publications transactionnelles dans la base de données.  
  
 **Agent de lecture de la file d'attente**  
 Affiché pour les publications transactionnelles qui autorisent les abonnements pouvant être mis à jour. Cliquez sur **les paramètres de sécurité** pour spécifier les paramètres de sécurité dans le **sécurité de l’Agent de lecture de file d’attente** boîte de dialogue. Une fois l'exécution de cet Assistant terminée, un Agent de lecture de la file d'attente est créé. Sa création ne dépend aucunement de la création d'abonnements mis à jour en file d'attente.  Si vous n'envisagez pas de créer des abonnements mis à jour en file d'attente , vous pouvez désactiver ce travail. Avec le bouton droit de la tâche (sous la forme : *[\< serveur de publication>]. \< entier>*.) dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent **travaux** puis cliquez sur **désactiver**.  
  
 Cliquez sur **aide** sur la **sécurité de l’Agent de lecture de file d’attente** boîte de dialogue pour plus d’informations sur les autorisations requises pour les comptes utilisés par l’Agent de lecture de file d’attente.  
  
> [!NOTE]  
>  Il existe un Agent de lecture de la file d'attente pour chaque base de données de distribution (et pour tous les serveurs de publication qu'il sert). Si une publication transactionnelle qui autorise les abonnements de mise à jour en attente existe déjà sur un serveur de publication, qui utilise une base de données de distribution donnée, les paramètres de sécurité sont en lecture seule. Vous pouvez modifier le compte sous lequel l’Agent de lecture de file d’attente s’exécute et établit des connexions dans le **des propriétés de serveur de distribution** boîte de dialogue, mais les modifications affectent les publications sur tous les serveurs de publication qui utilisent la base de données de distribution.  
  
## Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Créer un abonnement pouvant être mis à jour pour une publication transactionnelle](https://msdn.microsoft.com/library/mt740635.aspx)   
 [View and Modify Distributor and Publisher Properties](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Afficher et modifier les propriétés d'une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Gérer les connexions et les mots de passe dans la réplication](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Présentation des Agents de réplication](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  