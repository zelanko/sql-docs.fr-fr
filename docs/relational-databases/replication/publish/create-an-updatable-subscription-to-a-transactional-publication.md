---
title: "(Cr&#233;er un abonnement pouvant &#234;tre mis &#224; jour pour une publication transactionnelle (Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "07/21/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "à des abonnements transactionnels"
  - "abonnements transactionnels modifiables, SSMS"
ms.assetid: f9ef89ed-36f6-431b-8843-25d445ec137f
caps.latest.revision: 51
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 51
---
# (Cr&#233;er un abonnement pouvant &#234;tre mis &#224; jour pour une publication transactionnelle (Management Studio)

> [!NOTE]  
>  Cette fonctionnalité reste prise en charge dans les versions de [!INCLUDE[ssNoVersion_md](../../../includes/ssnoversion-md.md)] (2012 à 2016).  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
Configurer des abonnements à mettre à jour sur le **à abonnements** page de le **Assistant Nouvel abonnement**. Cette page est disponible seulement si vous avez activé une publication transactionnelle pour les abonnements pouvant être mis à jour. Pour plus d’informations sur l’activation à abonnements, consultez [Activer les abonnements mis à jour pour les Publications transactionnelles](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md).   
  
## Pour configurer un abonnement pouvant être mis à jour à partir du serveur de publication  

1. Se connecter au serveur de publication de Microsoft SQL Server Management Studio, puis développez le nœud du serveur.

2. Développez le dossier **Réplication** , puis développez le dossier **Publications locales** .

3. Cliquez sur une publication transactionnelle activée pour les abonnements mis à jour, puis cliquez sur **nouveaux abonnements**.

4. Suivez les pages de l'Assistant pour spécifier les options de l'abonnement, par exemple où l'Agent de distribution doit s'exécuter.

5. Sur le **à abonnements** page de le **Assistant Nouvel abonnement**, vérifiez **répliquer** est sélectionnée.

6. Sélectionnez une option dans le **valider sur le serveur de publication** liste déroulante :

    * Pour utiliser les abonnements avec mise à jour immédiate, sélectionnez **modifications simultanément**. Si vous sélectionnez cette option et que la publication autorise les abonnements mis à jour en file d’attente (la valeur par défaut pour les publications créées avec l’Assistant Nouvelle Publication), la propriété d’abonnement **update_mode** est définie sur **basculement**. Ce mode vous permet de passer ultérieurement en mise à jour en attente si nécessaire.

    * Pour utiliser les abonnements mis à jour en file d’attente, sélectionnez **modifications en file d’attente et valider dès que possible**. Si vous sélectionnez cette option, la publication autorise les abonnements de mise à jour immédiate (la valeur par défaut pour les publications créées avec l’Assistant Nouvelle Publication), et l’abonné exécute SQL Server 2005 ou une version ultérieure, la propriété d’abonnement **update_mode** est défini sur le basculement en file d’attente. Ce mode vous permet de passer ultérieurement en mise à jour immédiate si nécessaire.

    Pour plus d’informations sur le basculement entre les modes de mise à jour, consultez [commutateur entre les Modes mise à jour d’un abonnement transactionnel actualisable](../../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

7. Le **connexion pour mettre à jour les abonnements** page s’affiche pour les abonnements qui utilisent la mise à jour immédiate ou aient **update_mode** la valeur **en file d’attente de basculement**. Sur le **connexion pour mettre à jour les abonnements** page, spécifiez un serveur lié sur lequel les connexions au serveur de publication sont établies pour les abonnements de mise à jour immédiate. Les connexions sont utilisées par les déclencheurs qui s'exécutent pour l'abonné et propagent les modifications sur le serveur de publication. Sélectionnez l'une des options suivantes :

    * **Créer un serveur lié qui se connecte à l’aide de l’authentification SQL Server.** Sélectionnez cette option si vous n'avez pas défini un serveur distant ou un serveur lié entre l'Abonné et le serveur de publication. La réplication crée un serveur lié pour vous. Le compte que vous spécifiez doit déjà exister sur le serveur de publication.

    * **Utiliser un serveur lié ou un serveur distant que vous avez déjà défini.** Sélectionnez cette option si vous avez défini un serveur distant ou lié entre l’abonné et le serveur de publication à l’aide [sp_addserver (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md), [sp_addlinkedserver (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md), SQL Server Management Studio ou une autre méthode.

    Pour plus d’informations sur les autorisations requises par le compte du serveur lié, consultez le **en file d’attente de la mise à jour des abonnements** de [Entrez la description du lien ici](../../../relational-databases/replication/security/secure-the-subscriber.md).

8. Terminez l'Assistant.

## Pour configurer un abonnement pouvant être mis à jour à partir de l'Abonné


1. Se connecter à l’abonné dans SQL Server Management Studio, puis développez le nœud du serveur.

2. Développez le dossier **Réplication** .

3. Cliquez sur le **abonnements locaux** puis cliquez sur **nouveaux abonnements**.

4. Sur le **Publication** page de le **Assistant Nouvel abonnement**, sélectionnez **trouver de serveur de publication SQL Server** à partir de la **Publisher** liste déroulante.

5. Connectez-vous au serveur de publication dans la boîte de dialogue **Se connecter au serveur** .

6. Sélectionnez une publication transactionnelle activée pour les abonnements mis à jour sur la **Publication** page.

7. Suivez les pages de l'Assistant pour spécifier les options de l'abonnement, par exemple où l'Agent de distribution doit s'exécuter.

8. Sur le **à abonnements** page de l’Assistant Nouvel abonnement, vérifiez **répliquer** est sélectionnée.

9. Sélectionnez une option dans le **valider sur le serveur de publication** liste déroulante :

    * Pour utiliser les abonnements avec mise à jour immédiate, sélectionnez **modifications simultanément**. Si vous sélectionnez cette option et que la publication autorise les abonnements mis à jour en file d’attente (la valeur par défaut pour les publications créées avec l’Assistant Nouvelle Publication), la propriété d’abonnement **update_mode** est définie sur **basculement**. Ce mode vous permet de passer ultérieurement en mise à jour en attente si nécessaire.

    * Pour utiliser les abonnements mis à jour en file d’attente, sélectionnez **modifications en file d’attente et valider dès que possible**. Si vous sélectionnez cette option, la publication autorise les abonnements de mise à jour immédiate (la valeur par défaut pour les publications créées avec l’Assistant Nouvelle Publication), et l’abonné exécute SQL Server 2005 ou une version ultérieure, la propriété d’abonnement **update_mode** est définie en file d’attente à **basculement**. Ce mode vous permet de passer ultérieurement en mise à jour immédiate si nécessaire.

    Pour plus d’informations sur le basculement entre les modes de mise à jour, consultez [commutateur entre les Modes mise à jour d’un abonnement transactionnel actualisable](../../../relational-databases/replication/administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

10. Le **connexion pour mettre à jour les abonnements** page s’affiche pour les abonnements qui utilisent la mise à jour immédiate ou aient **update_mode** définis à en attente **basculement**. Sur le **connexion pour mettre à jour les abonnements** page, spécifiez un serveur lié sur lequel les connexions au serveur de publication sont établies pour les abonnements de mise à jour immédiate. Les connexions sont utilisées par les déclencheurs qui s'exécutent pour l'abonné et propagent les modifications sur le serveur de publication. Sélectionnez l'une des options suivantes :

    * **Créer un serveur lié qui se connecte à l’aide de l’authentification SQL Server.** Sélectionnez cette option si vous n'avez pas défini un serveur distant ou un serveur lié entre l'Abonné et le serveur de publication. La réplication crée un serveur lié pour vous. Le compte que vous spécifiez doit déjà exister sur le serveur de publication.

    * **Utiliser un serveur lié ou un serveur distant que vous avez déjà défini.** Sélectionnez cette option si vous avez défini un serveur distant ou lié entre l’abonné et le serveur de publication à l’aide [sp_addserver (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md), [sp_addlinkedserver (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md), SQL Server Management Studio ou une autre méthode.

    Pour plus d’informations sur les autorisations requises par le compte du serveur lié, consultez le **en file d’attente de la mise à jour des abonnements** de [Entrez la description du lien ici](../../../relational-databases/replication/security/secure-the-subscriber.md).

11. Terminez l'Assistant.

## Voir aussi

[Updatable Subscriptions for Transactional Replication](../../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)

[Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)

[Créer un abonnement pouvant être mis à jour sur une publication transactionnelle à l’aide de Transact-SQL](../../../relational-databases/replication/publish/create-updatable-subscription-to-transactional-publication.md) 
