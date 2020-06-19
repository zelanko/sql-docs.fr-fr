---
title: Distributed Replay d’installation (programme d’installation) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 64479cdc-661a-4e32-a381-8f8b5a238337
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1e91b1b3af5c8531800f60478a4cb31d31ac3fbc
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85054749"
---
# <a name="install-distributed-replay-setup"></a>Installer Distributed Replay (programme d'installation)
  Installer les fonctionnalités [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay avec l’Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Pour décider de l'emplacement où installer ces fonctionnalités, tenez compte des éléments suivants :  
  
-   Vous pouvez installer l'outil d'administration sur le même ordinateur que le contrôleur Distributed Replay ou sur d'autres ordinateurs.  
  
-   Chaque environnement Distributed Replay ne doit contenir qu'un seul contrôleur.  
  
-   Vous pouvez installer le service client sur 16 ordinateurs (physiques ou virtuels) au maximum.  
  
-   Une seule instance du service client peut être installée sur l'ordinateur du contrôleur Distributed Replay. Si votre environnement Distributed Replay doit avoir plusieurs clients, il n'est pas recommandé d'installer le service client sur le même ordinateur que le contrôleur. Cela risquerait de réduire la vitesse globale de Distributed Replay.  
  
-   Pour les scénarios de test des performances, nous déconseillons d'installer l'outil d'administration, le service du contrôleur ou le service client Distributed Replay sur l'instance cible de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'installation de toutes ces fonctionnalités sur le serveur cible doit être limitée au test fonctionnel de compatibilité des applications.  
  
-   Après l'installation, le service contrôleur, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller, doit s'exécuter avant le démarrage du service Distributed Replay Client sur les clients.  
  
> [!NOTE]  
>  Pour supprimer ou modifier des fonctionnalités Distributed Replay, utilisez la fenêtre **Programmes et fonctionnalités** du **Panneau de configuration**Windows. Sélectionnez [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] dans la fenêtre **Désinstaller ou modifier un programme** , puis cliquez sur **Supprimer** pour ouvrir l'Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Dans la page **Sélectionner les composants** , sélectionnez les fonctionnalités Distributed Replay à supprimer.  
  
 **Configuration requise :**  
  
-   Assurez-vous que les ordinateurs que vous voulez utiliser présentent la configuration décrite dans la rubrique [Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md).  
  
-   Avant d'entamer cette procédure, créez les comptes d'utilisateur de domaine sous lesquels s'exécuteront les services du contrôleur et du client. Il est préférable que ces comptes ne soient pas membres du groupe Administrateurs Windows. Pour plus d'informations, consultez la section relative aux comptes d'utilisateur et de service de la rubrique [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md) .  
  
    > [!NOTE]  
    >  Vous pouvez utiliser des comptes d'utilisateur locaux si vous exécutez l'outil d'administration, le service du contrôleur et le service du client sur le même ordinateur.  
  
 **Emplacements d'installation**  
  
 En supposant que vous utilisez les emplacements de fichiers et l'installation par défaut, le répertoire de base se trouve dans C:\Program Files\Microsoft SQL Server. Dans ce répertoire, les emplacements d'installation des binaires et des assemblys sont les suivants :  
  
-   Sur un système 32 bits :  
  
     [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Outils  
  
     \- OR -  
  
     \<Share Feature Directory>\Tools \\ (autre répertoire des fonctionnalités partagées fourni par l’utilisateur)  
  
-   Sur un système 64 bits :  
  
     C:\Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (x86) \120\Tools  
  
     \- OR -  
  
     \<Share Feature Directory (x86)>\Tools \\ (répertoire des fonctionnalités partagées de remplacement fourni par l’utilisateur (x86))  
  
### <a name="to-install-distributed-replay-features"></a>Pour installer les fonctionnalités Distributed Replay  
  
1.  Pour démarrer l'installation d'une fonctionnalité Distributed Replay, démarrez l'Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
2.  La page **Règles de support du programme d'installation** identifie les problèmes susceptibles de se présenter lors de l'installation des fichiers de support d'installation de SQL Server. Vous devez corriger toute erreur de support du programme d'installation avant de poursuivre l'installation.  
  
3.  Dans la page **Clé du produit** , sélectionnez une case d'option pour indiquer si vous installez une édition gratuite de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ou une version de production du produit qui a une clé PID. Pour plus d’informations, consultez [éditions et composants de SQL Server 2014](../editions-and-components-of-sql-server-2016.md).  
  
4.  Dans la page **Termes du contrat de licence** , prenez connaissance du contrat de licence, puis activez la case à cocher indiquant que vous en acceptez les termes et conditions. Pour aider à améliorer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez également activer l'option d'utilisation des fonctionnalités et envoyer des rapports à [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
5.  Dans la page **Fichiers de support du programme d'installation** , cliquez sur **Installer** pour installer ou mettre à jour les fichiers de support du programme d'installation pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
6.  Dans la page **Rôle d’installation**, sélectionnez **Installation de fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]** , puis cliquez sur **Suivant** pour passer à la page **Sélection des fonctionnalités**.  
  
7.  Dans la page **Sélection de fonctionnalités** , configurez les fonctionnalités à installer.  
  
    -   Pour installer l’outil d’administration, sélectionnez **Outils de gestion - De base**.  
  
    -   Pour installer le service du contrôleur, sélectionnez **Distributed Replay Controller**.  
  
    -   Pour installer le service client, sélectionnez **Distributed Replay Client**.  
  
     **Important !** lorsque vous configurez le contrôleur Distributed Replay, vous pouvez spécifier un ou plusieurs comptes d'utilisateurs qui seront utilisés pour exécuter les services client Distributed Replay. Vous trouverez ci-dessous la liste des comptes pris en charge :  
  
    -   Compte d’utilisateur de domaine  
  
    -   Compte d'utilisateur local créé par l'utilisateur  
  
    -   Administrateur  
  
    -   Compte virtuel et Compte de service administré (MSA)  
  
    -   Services réseau, Services locaux et Système  
  
     Les comptes de groupe (locaux ou de domaine) et autres comptes intégrés (comme Tout le monde) ne sont pas acceptés.  
  
8.  Éventuellement, cliquez sur le bouton de sélection (...) pour modifier le chemin du répertoire des fonctionnalités partagées.  
  
    1.  Sur les ordinateurs 32 bits, le chemin d’installation par défaut est **C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**  
  
    2.  Sur les ordinateurs 64 bits, le chemin d’installation par défaut est **C:\Program Files (x86)\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\**  
  
9. Quand vous avez terminé, cliquez sur **Suivant**.  
  
10. Dans la page **Règles d'installation** , le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide la configuration de votre ordinateur. Une fois que le processus de validation est terminé, cliquez sur **Suivant**.  
  
11. La page **Espace disque nécessaire** calcule l'espace disque nécessaire pour les fonctionnalités que vous spécifiez. Elle compare ensuite cet espace à l'espace disque disponible.  
  
12. Dans la page **Création de rapports d'erreurs** , spécifiez les informations que vous souhaitez envoyer à [!INCLUDE[msCoName](../../includes/msconame-md.md)] afin d'aider à améliorer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L'option de création de rapports d'erreurs est activée par défaut.  
  
13. Dans la page **Règles de configuration de l'installation** , l'Outil d'analyse de configuration système exécutera un autre ensemble de règles pour valider la configuration de votre ordinateur avec les fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous avez spécifiées.  
  
14. Dans la page **Prêt à installer le programme** , cliquez sur **Installer**.  
  
    > [!IMPORTANT]  
    >  Une fois que vous avez installé Distributed Replay, vous devez créer des règles de pare-feu sur le contrôleur et les ordinateurs clients, et accorder des autorisations à chaque ordinateur client sur le serveur cible. Pour plus d’informations, consultez [Suivre les étapes consécutives à l’installation](../../tools/distributed-replay/complete-the-post-installation-steps.md).  
  
 Ces rubriques supplémentaires décrivent d'autres façons d'installer Distributed Replay :  
  
-   [Installer Distributed Replay à partir de l’invite de commandes](../../tools/distributed-replay/install-distributed-replay-overview.md)  
  
-   [Installer Distributed Replay à l’aide d’un fichier de configuration](../../../2014/sql-server/install/install-distributed-replay-using-a-configuration-file.md)  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
 Vous devez posséder des autorisations administratives pour installer les fonctionnalités de Distributed Replay. Seule une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] disposant d’autorisations sysadmin peut ajouter des comptes de services clients au rôle serveur sysadmin du serveur de test. Pour plus d'informations sur les questions de sécurité de Distributed Replay, consultez [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)   
 [Distributed Replay Requirements](../../tools/sql-server-profiler/replay-requirements.md)   
 [Options de ligne de commande de l’outil d’administration &#40;Distributed Replay Utility&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md)   
 [Configurer Distributed Replay](../../tools/distributed-replay/configure-distributed-replay.md)  
  
  
