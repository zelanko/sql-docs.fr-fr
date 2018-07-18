---
title: 'Leçon 1 : Création de comptes Windows pour la réplication | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: a3bd3b0369c990b6db3dc1cbb44f7fd387289ce9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37303649"
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a>Leçon 1 : Création de comptes Windows pour la réplication
  Dans cette leçon, vous allez créer des comptes Windows pour exécuter les agents de réplication. Vous allez créer un compte Windows distinct sur le serveur local pour les agents suivants :  
  
|Agent|Emplacement|Nom du compte|  
|-----------|--------------|------------------|  
|Agent d'instantané|Serveur de publication|\<*nom_ordinateur*>\repl_snapshot|  
|l'Agent de lecture du journal ;|Serveur de publication|\<*nom_ordinateur*>\repl_logreader|  
|Agent de distribution|Serveur de publication et Abonné|\<*nom_ordinateur*>\repl_distribution|  
|Agent de fusion|Serveur de publication et Abonné|\<*nom_ordinateur*>\repl_merge|  
  
> [!NOTE]  
>  Dans les didacticiels de réplication, le serveur de publication et le serveur de distribution partagent la même instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le serveur de publication et l'Abonné peuvent partager la même instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais ce n'est pas une obligation. Si le serveur de publication et l'Abonné partagent la même instance, les étapes de création de comptes pour l'Abonné ne sont pas requises.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>Pour créer des comptes Windows locaux pour les agents de réplication sur le serveur de publication  
  
1.  Sur le serveur de publication, dans le Panneau de configuration, dans **Outils d’administration** , ouvrez **Gestion de l’ordinateur** .  
  
2.  Dans **Outils système**, développez **Utilisateurs et groupes locaux**.  
  
3.  Cliquez avec le bouton droit sur **Utilisateurs** , puis cliquez sur **Nouvel utilisateur**.  
  
4.  Entrez `repl_snapshot` dans le **nom d’utilisateur** zone, fournissez le mot de passe et d’autres informations pertinentes, puis cliquez sur **créer** pour créer le compte repl_snapshot.  
  
5.  Répétez l'étape précédente pour créer les comptes repl_logreader, repl_distribution et repl_merge.  
  
6.  Cliquez sur **Fermer**.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>Pour créer des comptes Windows locaux pour les agents de réplication sur l'Abonné  
  
1.  Sur l’Abonné, dans le Panneau de configuration, dans **Outils d’administration** , ouvrez **Gestion de l’ordinateur** .  
  
2.  Dans **Outils système**, développez **Utilisateurs et groupes locaux**.  
  
3.  Cliquez avec le bouton droit sur **Utilisateurs** , puis cliquez sur **Nouvel utilisateur**.  
  
4.  Entrez `repl_distribution` dans le **nom d’utilisateur** zone, fournissez le mot de passe et d’autres informations pertinentes, puis cliquez sur **créer** pour créer le compte repl_distribution.  
  
5.  Répétez l'étape précédente pour créer le compte repl_merge.  
  
6.  Cliquez sur **Fermer**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez créé avec succès les comptes Windows des agents de réplication. Ensuite, vous allez configurer le dossier d'instantanés. Voir [Leçon 2 : Préparation du dossier d’instantanés](lesson-2-preparing-the-snapshot-folder.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des Agents de réplication](agents/replication-agents-overview.md)  
  
  
