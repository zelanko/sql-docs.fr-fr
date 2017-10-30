---
title: "Boîte de dialogue Créer un compte et un profil de messagerie de base de données | Microsoft Docs"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.mds.configmanager.dbmailprofileacct.f1
ms.assetid: b93ea3d4-9f22-490e-8e26-d766b454aed6
caps.latest.revision: 7
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 240967b3909a2b3796534cb29c42dfa5838be692
ms.contentlocale: fr-fr
ms.lasthandoff: 09/07/2017

---
# <a name="create-database-mail-profile-and-account-dialog-box"></a>Boîte de dialogue Créer un compte et un profil de messagerie de base de données
  Utilisez la boîte de dialogue **Créer un compte et un profil de messagerie de base de données** pour créer un profil de messagerie de base de données et un compte de messagerie de base de données pour la base de données des [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Ce profil sera utilisé pour avertir les utilisateurs et les groupes par courrier électronique lorsque la validation des règles d'entreprise échoue.  
  
## <a name="database-mail-profile-and-account"></a>Compte et profil de messagerie de base de données  
 Un *profil de messagerie de base de données* est une collection de comptes de messagerie de base de données. Un *compte de messagerie de base de données* contient les informations utilisées par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour l’envoi d’e-mails à un serveur SMTP. Lorsque vous créez le profil et le compte dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], le compte est ajouté automatiquement au profil et les informations sur ce compte sont utilisées pour envoyer des messages électroniques.  
  
> [!NOTE]  
>  Vous ne pouvez pas utiliser le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] pour mettre à jour des profils ou des comptes de messagerie de base de données existants, ni configurer plusieurs comptes pour un profil. Pour effectuer des tâches plus avancées avec la messagerie de base de données, vous pouvez utiliser [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou des scripts Transact-SQL. Pour plus d’informations, consultez la section [Objets de configuration de la messagerie de base de données](../relational-databases/database-mail/database-mail-configuration-objects.md) dans la documentation en ligne de SQL Server.  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Nom de profil**|Entrez un nom pour le nouveau profil de messagerie de base de données. Ce nom doit être unique parmi les profils de messagerie de base de données configurés pour la base de données des [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .<br /><br /> Une fois que vous avez créé ce profil, il est disponible et sélectionné dans la page **Base de données** dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)].|  
|**Nom du compte**|Entrez un nom pour le nouveau compte de messagerie de base de données à associer à ce profil. Ce nom doit être unique parmi les comptes de messagerie de base de données configurés pour la base de données des [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Ce compte ne constitue ni un compte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ni un compte d’utilisateur Windows.|  
  
## <a name="outgoing-smtp-mail-server"></a>Serveur de courrier sortant (SMTP)  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Adresse de messagerie**|Tapez le nom de l'adresse de messagerie du compte. Il s’agit de l’adresse e-mail à partir de laquelle cet e-mail est envoyé, dont le format doit être *nom_e-mail*@*nom_domaine*. Un exemple d’adresse e-mail est sales@contoso.com.|  
|**Nom complet**|Paramètre facultatif. Tapez le nom à afficher sur les messages électroniques envoyés à partir de ce compte. Un exemple de nom complet est Contoso Sales Group.|  
|**Adresse de messagerie pour la réponse**|Paramètre facultatif. Tapez l'adresse de messagerie à utiliser pour répondre aux messages envoyés à partir de ce compte. Un exemple d’adresse de réponse est admin@contoso.com.|  
|**Serveur SMTP**|Tapez le nom ou l’adresse IP du serveur SMTP utilisé par le compte pour envoyer des e-mails. Un exemple de format de serveur SMTP est **smtp.***<nom_société>***.com**. Pour plus d'informations, contactez l'administrateur de messagerie.|  
|**Numéro de port**|Tapez le numéro de port du serveur SMTP de ce compte. Le port SMTP par défaut est le port 25.|  
|**Ce serveur demande une connexion sécurisée (SSL)**|Chiffre la communication au moyen de SSL (Secure Sockets Layer).|  
  
## <a name="smtp-authentication"></a>Authentification SMTP  
 Le courrier de la messagerie de base de données peut être envoyé à l’aide des informations d’identification du [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)], d’autres informations d’identification que vous fournissez, ou de façon anonyme. À titre de recommandation, si votre serveur de messagerie nécessite une authentification, créez un compte d’utilisateur spécifique à utiliser pour la messagerie de base de données. Ce compte d'utilisateur doit disposer d'autorisations minimales et ne doit pas être utilisé à d'autres fins.  
  
|Nom du contrôle|Description|  
|------------------|-----------------|  
|**Authentification Windows à l'aide d'informations d'identification du service de moteur de bases de données**|Spécifiez que la messagerie de base de données doit utiliser les informations d’identification du compte de service Windows [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] pour l’authentification sur le serveur SMTP.|  
|**Authentification de base**|Spécifiez que la messagerie de base de données doit utiliser un nom d'utilisateur et un mot de passe spécifiques pour l'authentification sur le serveur SMTP. Ces informations sont utilisées uniquement pour l’authentification avec le serveur de messagerie, et le compte n’a pas besoin de correspondre à un utilisateur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ni à un utilisateur sur l’ordinateur qui exécute [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
|**Nom d'utilisateur**|Tapez le nom du compte d'utilisateur que la messagerie de base de données utilise pour se connecter au serveur SMTP. Un nom d'utilisateur est obligatoire si le serveur SMTP nécessite une authentification de base.|  
|**Mot de passe**|Tapez le mot de passe que la messagerie de base de données utilise pour se connecter au serveur SMTP. Un mot de passe est obligatoire si le serveur SMTP nécessite une authentification de base.|  
|**Confirmer le mot de passe**|Tapez une seconde fois le mot de passe pour le valider.|  
|**Authentification anonyme**|Spécifiez que le serveur SMTP ne requiert pas d'authentification. La messagerie de base de données n'utilise pas d'informations d'identification pour s'authentifier sur le serveur SMTP.|  
  
## <a name="see-also"></a>Voir aussi  
 [Page Configuration de base de données &#40;Gestionnaire de configuration Master Data Services&#41;](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
[Installation et configuration de Master Data Services](../master-data-services/master-data-services-installation-and-configuration.md)
  
  

