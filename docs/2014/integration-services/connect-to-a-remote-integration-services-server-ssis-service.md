---
title: Se connecter à un serveur de Integration Services distant (service SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- service [Integration Services], remote instance
- Integration Services service, connecting
- Integration Services service, remote instance
- service [Integration Services], connecting
ms.assetid: 9487aff1-44d8-42c1-8176-bb9891d4632d
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 0b9fa3f54b7b16b1fd397bfe80c95d08e39289eb
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84921367"
---
# <a name="connect-to-a-remote-integration-services-server-ssis-service"></a>Se connecter à un serveur Integration Services distant (Service SSIS)
    
> [!IMPORTANT] 
> Cette rubrique présente le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , un service Windows qui permet de gérer les packages [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] prend en charge le service pour la compatibilité avec les versions antérieures de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. À compter de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], vous pouvez gérer des objets tels que des packages sur le serveur Integration Services.  
  
 Pour se connecter à une instance de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur un serveur distant, que ce soit à partir de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou d’une autre application de gestion, les utilisateurs de l’application ont besoin d’un ensemble de droits sur le serveur.  
  
> [!IMPORTANT] 
> Pour gérer les packages stockés sur un serveur distant, vous n’avez pas besoin de vous connecter à l’instance du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] de ce serveur distant. Au lieu de cela, modifiez le fichier de configuration du service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] afin que [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] affiche les packages stockés sur le serveur distant. Pour plus d’informations, consultez [Configuration du service Integration Services &#40;Service SSIS&#41;](service/integration-services-service-ssis-service.md).  
  
## <a name="connecting-to-integration-services-on-a-remote-server"></a>Connexion à Integration Services sur un serveur distant  
  
#### <a name="to-connect-to-integration-services-on-a-remote-server"></a>Pour se connecter à Integration Services sur un serveur distant  
  
1.  Ouvrez [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  Sélectionnez **Fichier**et **Connecter l’Explorateur d’objets** pour afficher la boîte de dialogue **Se connecter au serveur** .  
  
3.  Sélectionnez **Integration Services** dans la liste **Type de serveur** .  
  
4.  Tapez le nom d’un serveur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] dans la zone de texte **Nom du serveur**.  
  
    > [!NOTE]  
    >  Le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] n'est pas spécifique à l'instance. Vous vous connectez au service en utilisant le nom de l'ordinateur sur lequel le service Integration Services s'exécute.  
  
5.  Cliquez sur **Connecter**.  
  
> [!NOTE]  
>  La boîte de dialogue **Rechercher les serveurs** n’affiche pas les instances distantes de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. De plus, les options disponibles sous l’onglet **Options de connexion** de la boîte de dialogue **Se connecter au serveur** (cliquez sur le bouton **Options** pour les afficher) ne s’appliquent pas aux connexions [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
## <a name="eliminating-the-access-is-denied-error"></a>Suppression de l'erreur « Accès refusé »  
 Lorsqu'un utilisateur muni des droits suffisants tente de se connecter à une instance de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur un serveur distant, ce dernier répond par un message d'erreur lui indiquant que l'accès est refusé. Vous pouvez éviter ce message d'erreur en vous assurant que les utilisateurs bénéficient des autorisations DCOM requises.  
  
#### <a name="to-configure-rights-for-remote-users-on-windows-server-2003-or-windows-xp"></a>Pour configurer les droits des utilisateurs distants dans Windows Server 2003 ou Windows XP  
  
1.  Si l'utilisateur n'est pas membre du groupe Administrateurs local, ajoutez l'utilisateur au groupe des utilisateurs Distributed COM. Pour ce faire, vous pouvez utiliser le composant logiciel enfichable MMC Gestion de l’ordinateur accessible à partir du menu **Outils d’administration** .  
  
2.  Ouvrez le Panneau de configuration, double-cliquez sur **Outils d’administration** , puis sur **Services de composants** pour démarrer le composant logiciel enfichable MMC Services de composants.  
  
3.  Développez le nœud **Services de composants** dans le volet gauche de la console. Développez le nœud **Ordinateurs** et **Poste de travail**, puis cliquez sur le nœud **Configuration DCOM** .  
  
4.  Sélectionnez le nœud **Configuration DCOM** , puis sélectionnez SQL Server Integration Services 11.0 dans la liste des applications configurables.  
  
5.  Cliquez avec le bouton droit sur SQL Server Integration Services 11.0, puis sélectionnez **Propriétés**.  
  
6.  Dans la boîte de dialogue **Propriétés de SQL Server Integration Services 11.0** , sélectionnez l’onglet **Sécurité** .  
  
7.  Sous **Autorisations d’exécution et d’activation**, sélectionnez **Personnaliser**, puis cliquez sur **Modifier** pour ouvrir la boîte de dialogue **Autorisation d’exécution** .  
  
8.  Dans la boîte de dialogue **Autorisation d’exécution** , ajoutez ou supprimez des utilisateurs, puis affectez les autorisations appropriées aux utilisateurs et groupes concernés. Les autorisations disponibles sont Exécution locale, Exécution à distance, Activation locale et Activation à distance. Les droits d'exécution octroient ou refusent l'autorisation de démarrer et d'arrêter le service ; les droits d'activation octroient ou refusent l'autorisation de se connecter au service.  
  
9. Cliquez sur OK pour fermer la boîte de dialogue.  
  
10. Sous **Autorisations d’accès**, répétez les étapes 7 et 8 pour assigner les autorisations appropriées aux utilisateurs et groupes concernés.  
  
11. Fermez le composant logiciel enfichable MMC.  
  
12. Redémarrez le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
#### <a name="to-configure-rights-for-remote-users-on-windows-2000-with-the-latest-service-packs"></a>Pour configurer les droits des utilisateurs distants dans Windows 2000 avec les derniers Service Packs  
  
1.  Exécutez **dcomcnfg.exe** à l’invite de commandes.  
  
2.  Dans la page **Applications** de la boîte de dialogue des **propriétés de configuration de Distributed COM** , sélectionnez SQL Server Integration Services 11.0, puis cliquez sur **Propriétés**.  
  
3.  Sélectionnez la page **Security** .  
  
4.  Utilisez les deux boîtes de dialogue distinctes pour configurer les **autorisations d’accès** et les **autorisations d’exécution**. Aucune distinction entre accès local et accès à distance n'est possible : les autorisations d'accès englobent l'accès local et l'accès à distance, et les autorisations d'exécution incluent l'exécution locale et l'exécution à distance.  
  
5.  Fermez les boîtes de dialogue et **dcomcnfg.exe**.  
  
6.  Redémarrez le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
## <a name="connecting-by-using-a-local-account"></a>Connexion à l'aide d'un compte local  
 Si vous travaillez sous un compte Windows local sur un ordinateur client, vous pouvez vous connecter au service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur un ordinateur distant uniquement si un compte local porte le même nom et mot de passe et si les droits appropriés existent sur l'ordinateur distant.  
  
## <a name="by-default-the-ssis-service-does-not-support-delegation"></a>Par défaut, le service SSIS ne prend pas en charge la délégation  
Par défaut [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , le service ne prend pas en charge la délégation des informations d’identification, ou ce qui est parfois appelé double saut. Dans ce scénario, vous opérez sur un ordinateur client, le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] s’exécute sur un deuxième ordinateur et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] s’exécute sur un troisième. Dans un premier temps, [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] transmet avec succès vos informations d’identification de l’ordinateur client au deuxième ordinateur sur lequel le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] s’exécute. En revanche, le service [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ne peut pas déléguer vos informations d’identification du deuxième ordinateur au troisième sur lequel [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] s’exécute.

Vous pouvez activer la délégation des informations d’identification en octroyant le droit **Approuver cet utilisateur pour la délégation à tous les services (Kerberos uniquement)** au compte de service SQL Server, qui lance le service Integration Services (ISServerExec.exe) en tant que processus enfant. Avant d’octroyer ce droit, demandez-vous s’il est conforme aux exigences de sécurité de votre organisation.

Pour plus d’informations, consultez [Getting Cross Domain Kerberos and Delegation working with SSIS Package](https://blogs.msdn.microsoft.com/psssql/2014/06/26/getting-cross-domain-kerberos-and-delegation-working-with-ssis-package/)(Faire fonctionner Kerberos et la délégation entre domaines avec un package SSIS).
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un Pare-feu Windows pour l'accès au service SSIS](../../2014/integration-services/configure-a-windows-firewall-for-access-to-the-ssis-service.md)  
  
  
