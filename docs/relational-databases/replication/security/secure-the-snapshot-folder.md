---
title: Sécuriser le dossier d’instantanés | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], security
ms.assetid: 3cd877d1-ffb8-48fd-a72b-98eb948aad27
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a73ae886682890c68c34ac90af33438d7f7b9644
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54124179"
---
# <a name="secure-the-snapshot-folder"></a>Sécuriser le dossier d'instantanés
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le dossier d'instantané est un répertoire qui stocke les fichiers d'instantanés ; il vous est recommandé de dédier ce dossier au stockage des instantanés. Accordez à l'Agent d'instantané l'autorisation d'écriture sur ce dossier, et assurez-vous que l'autorisation de lecture n'est accordée qu'au compte Windows qu'utilise l'Agent de fusion ou l'Agent de distribution lorsqu'il accède à ce dossier. Pour accéder à un dossier d'instantané situé sur un ordinateur distant, le compte Windows associé à l'Agent doit être un compte de domaine.  
  
> [!NOTE]  
>  Le contrôle de compte d'utilisateur (UAC) aide les administrateurs à gérer leurs droits utilisateur élevés (parfois appelés *privilèges*). Dans les systèmes d'exploitation dans lesquels le contrôle de compte d'utilisateur est activé, les administrateurs n'utilisent pas leurs droits d'administration. À la place, ils effectuent la plupart des actions en tant qu'utilisateurs standard (non administratifs), assumant temporairement leurs droits d'administration seulement lorsque cela est nécessaire. La fonctionnalité Contrôle de compte d'utilisateur peut empêcher l'accès administratif au partage de fichiers d'instantanés. Vous devez donc octroyer explicitement des autorisations sur le partage de fichiers d'instantanés aux comptes Windows qui sont utilisés par l'Agent d'instantané, l'Agent de distribution et l'Agent de fusion. Vous devez effectuer cette opération même si les comptes Windows sont membres du groupe Administrateurs.  
  
 Lorsque vous configurez un serveur de distribution au moyen de l'Assistant Configuration de distribution ou de l'Assistant Nouvelle publication, le dossier d'instantané est installé par défaut sur un chemin local : X:\Program Files\Microsoft SQL Server\\*\<instance>* \MSSQL\ReplData. Si vous utilisez un serveur de distribution distant ou des abonnements par extraction, vous devez spécifier un partage réseau UNC (tel que \\\\<*nom_ordinateur>* \snapshot) plutôt qu’un chemin local.  
  
 Lorsque vous accordez des autorisations d'accès au dossier d'instantané, faites-le en fonction du mode d'accès au dossier. Les onglets de boîte de dialogue suivants sont utilisés dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows 2003 :  
  
-   Si vous spécifiez un chemin local, accordez les autorisations dans l'onglet **Sécurité** de la boîte de dialogue **Propriétés** du dossier.  
  
-   Si vous spécifiez un partage réseau, accordez les autorisations dans l'onglet **Partage** de la boîte de dialogue **Propriétés** du dossier.  
  
    > [!NOTE]  
    >  Si l'agent de réplication est exécuté sur le serveur de distribution, utilisez les options de l'onglet **Sécurité** (boîte de dialogue **Propriétés** ) du dossier pour accorder des autorisations au compte Windows servant à l'exécution de l'agent. Faites-le même si vous utilisez un partage réseau. Cette situation concerne l'Agent de fusion et l'Agent de distribution dans le cadre d'un abonnement par envoi de données (push) et l'Agent d'instantané lorsque les serveurs de publication et de distribution se trouvent sur le même ordinateur.  
  
 Pour plus d'informations sur la définition d'autorisations pour les chemins locaux et les partages réseau, consultez la documentation Windows.  
  
> [!NOTE]  
>  Si une publication est abandonnée, la réplication tente de supprimer le dossier d'instantané dans le contexte de sécurité du compte de service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Si ce compte ne détient pas les privilèges suffisants, connectez-vous à l'aide d'un compte qui dispose des bons privilèges et supprimez le dossier manuellement. La suppression d'un dossier nécessite le privilège **Modification** si le dossier a un chemin local, et le privilège **Contrôle total** si le dossier a un chemin réseau.  
  
## <a name="delivering-snapshots-through-ftp"></a>Remise d'instantanés via FTP  
 Une pratique de sécurité vous recommande de stocker les instantanés dans un partage UNC, mais ils peuvent également être stockés dans un partage FTP puis remis à un Abonné via FTP. Lors de la configuration du serveur FTP, assurez-vous que le répertoire virtuel expose un partage UNC sous-jacent qui accorde à l'Agent d'instantané un accès en écriture pour la publication.  
  
 Pour configurer un Abonné pour qu'il récupère l'instantané via FTP, commencez par configurer un serveur FTP avec un nom de connexion et un mot de passe FTP donnant aux Abonnés un accès en lecture (ou accès « get ») pour leur permettre de télécharger les fichiers d'instantanés.  
  
 Pour remettre des instantanés via FTP, consultez [Remettre un instantané via FTP](../../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).  
  
 Pour plus d'informations sur la définition et la modification du mot de passe d'accès aux instantanés via FTP, consultez la section « Remise d'instantanés via FTP » dans [Secure the Publisher](../../../relational-databases/replication/security/secure-the-publisher.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Modifier les options des instantanés](../../../relational-databases/replication/snapshot-options.md)   
 [Initialiser un abonnement avec un instantané](../../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Afficher et modifier les paramètres de sécurité de la réplication](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)   
 [Transférer des instantanés via FTP](../../../relational-databases/replication//publish/deliver-a-snapshot-through-ftp.md)  
  
  
