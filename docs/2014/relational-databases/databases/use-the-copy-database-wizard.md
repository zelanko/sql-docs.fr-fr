---
title: Utiliser l’Assistant Copie de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.cdw.transfermethod.f1
- sql12.swb.cdw.welcome.f1
- sql12.swb.cdw.packageconfiguration.f1
- sql12.swb.cdw.schedule.f1
- sql12.swb.cdw.destination.f1
- sql12.swb.cdw.complete.f1
- sql12.swb.cdw.destinationconfiguration.f1
- sql12.swb.cdw.selectdatabaseobjects.f1
- sql12.swb.cdw.databases.f1
- sql12.swb.cdw.source.f1
- sql12.swb.cdw.locationofsourcedbfiles.f1
helpviewer_keywords:
- Copy Database Wizard
- starting Copy Database Wizard
ms.assetid: 7a999fc7-0a26-4a0d-9eeb-db6fc794f3cb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0baaeef6cb196a67b2f615aa280b61b61fbc5119
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970003"
---
# <a name="use-the-copy-database-wizard"></a>Utiliser l'Assistant Copie de base de données
  L'Assistant Copie de base de données vous permet de facilement déplacer ou copier des bases de données et leurs objets d'un serveur à un autre, sans nécessiter l'arrêt des serveurs. Vous pouvez également mettre à niveau les bases de données d'une version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. À l'aide de cet Assistant, vous pouvez effectuer les opérations suivantes :  
  
-   Choisir un serveur source et un serveur de destination.  
  
-   Sélectionner les bases de données à déplacer, à copier ou à mettre à niveau.  
  
-   Spécifier l'emplacement de fichier des bases de données.  
  
-   Créer des connexions sur le serveur de destination.  
  
-   Copier d'autres objets de support, travaux, procédures stockées définies par l'utilisateur et messages d'erreur.  
  
-   Programmer l'heure à laquelle déplacer ou copier les bases de données.  
  
 En plus de copier des bases de données, vous pouvez copier les métadonnées associées, par exemple, connexions et objets de la base de données **master** requis par une base de données copiée.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Composants requis](#Prerequisites)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Utilisation de l'Assistant Copie de base de données pour :**  
  
     [Copier, déplacer ou mettre à niveau des bases de données](#Copy_Move)  
  
-   **Suivi, après la mise à niveau :**  
  
     [Après la mise à niveau d'une base de données SQL Server](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   L'Assistant Copie de base de données n'est pas disponible dans l'édition Express.  
  
-   L'Assistant Copie de base de données ne peut pas être utilisé pour copier ou déplacer les bases de données suivantes.  
  
    -   Bases de données système  
  
    -   les bases de données marquées pour la réplication ;  
  
    -   les bases de données marquées comme Inaccessible, Chargement, Déconnecté, Récupération, Suspect ou en Mode Urgence.  
  
-   Après sa mise à niveau, une base de données ne peut pas être mise à niveau vers une version antérieure.  
  
-   Si vous sélectionnez l'option **Déplacer** , l'Assistant supprime automatiquement la base de données source après avoir déplacé la base de données. L'Assistant Copie de base de données ne supprime pas une base de données source si vous sélectionnez l'option **Copier** .  
  
-   Si vous utilisez la méthode [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object pour déplacer le catalogue de texte intégral, vous devez de nouveau remplir l’index après le déplacement.  
  
-   La méthode de détachement et d'attachement permet de détacher la base de données, de déplacer ou copier les fichiers .mdf, .ndf et .ldf de la base de données, puis de rattacher la base de données à son nouvel emplacement. En cas d'utilisation de la méthode de détachement et d'attachement, les sessions actives ne peuvent pas être attachées à la base de données en cours de déplacement ou de copie, ceci afin d'éviter une perte ou une incohérence des données. Si une session est active, l'Assistant Copie de base de données n'exécute pas l'opération de déplacement ou de copie. Dans le cas de la méthode [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Object, les sessions actives sont autorisées car la base de données n'est jamais placée en mode hors connexion.  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Conditions préalables  
 Vérifiez que SQL Server Agent est démarré sur le serveur de destination.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
  
-   Pour garantir une performance optimale de la base de données mise à niveau, exécutez sp_updatestats (mise à jour des statistiques) sur la base de données mise à niveau.  
  
-   Lorsque vous copiez une base de données sur une autre instance de serveur et il est possible que vous deviez recréer sur cette autre instance de serveur une partie ou l'ensemble des métadonnées de la base de données, telles que les connexions et les travaux, afin de garantir la cohérence pour les utilisateurs et les applications. Pour plus d’informations, consultez [Gérer les métadonnées durant la mise à disposition d’une base de données sur une autre instance de serveur &#40;SQL Server&#41;](manage-metadata-when-making-a-database-available-on-another-server.md).  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Vous devez être membre du rôle de serveur fixe **sysadmin** sur le serveur source et sur le serveur de destination.  
  
##  <a name="copy-move-or-upgrade-databases"></a><a name="Copy_Move"></a>Copier, déplacer ou mettre à niveau des bases de données  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l'Explorateur d'objets, développez **Bases de données**, cliquez avec le bouton droit sur une base de données, pointez sur **Tâches**, puis sélectionnez **Copier la base de données**.  
  
2.  Sur la page **Sélectionnez un serveur source** , spécifiez le serveur sur lequel se trouve la base de données que vous souhaitez déplacer ou copier, puis entrez les informations de connexion. Une fois la méthode d'authentification sélectionnée et les informations de connexion entrées, cliquez sur **Suivant** afin d'établir la connexion au serveur source. Cette connexion reste active tout au long de la session.  
  
     **Serveur source**  
     Sélectionnez le nom du serveur sur lequel se situent les bases de données que vous souhaitez déplacer ou copier, ou cliquez sur le bouton Parcourir (**...**) pour rechercher le serveur de votre choix. La version du serveur doit être au moins [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
     **Utiliser l'authentification Windows**  
     Permettre à un utilisateur de se connecter via un compte d'utilisateur [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
     **Utiliser l’authentification SQL Server**  
     Permettre à un utilisateur de se connecter en fournissant un nom d'utilisateur et un mot de passe d'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     **Nom d'utilisateur**  
     Entrez le nom d'utilisateur avec lequel se connecter. Cette option est disponible uniquement si vous avez choisi la connexion avec l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     **Mot de passe**  
     Entrez le mot de passe utilisé avec la connexion. Cette option est uniquement disponible si vous avez choisi la connexion avec l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     **Suivant**  
     Connectez-vous au serveur et validez l'utilisateur. Ce processus vérifie si l'utilisateur est membre du rôle de serveur fixe **sysadmin** sur l'ordinateur sélectionné.  
  
3.  Sur la page **Sélectionnez un serveur de destination** , spécifiez le serveur sur lequel la base de données sera déplacée ou copiée. Si vous spécifiez la même instance de serveur pour le serveur source et le serveur de destination, la base de données sera copiée. Dans ce cas, vous devrez renommer la base de données à une étape ultérieure de l'Assistant. Le nom de la base de données source ne peut être utilisé pour la base de données copiée ou déplacée que s'il n'y a pas de conflits de nom sur le serveur de destination. En cas de conflits de noms, vous devez les résoudre manuellement sur le serveur de destination avant de pouvoir y utiliser le nom de la base de données de source.  
  
     **Serveur de destination**  
     Sélectionnez le nom du serveur sur lequel vous souhaitez déplacer ou copier la ou les bases de données, ou cliquez sur le bouton Parcourir (**...**) pour rechercher un serveur de destination.  
  
    > [!NOTE]  
    >  Vous pouvez utiliser une destination qui est un serveur cluster ; l'Assistant Copie de base de données s'assurera que vous sélectionnez uniquement des lecteurs partagés sur un serveur de destination cluster.  
  
     **Utiliser l'authentification Windows**  
     Permettre à un utilisateur de se connecter via un compte d'utilisateur [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
     **Utiliser l’authentification SQL Server**  
     Permettre à un utilisateur de se connecter en fournissant un nom d'utilisateur et un mot de passe d'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     **Nom d'utilisateur**  
     Entrez le nom d'utilisateur avec lequel se connecter. Cette option est disponible uniquement si vous avez sélectionné l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     **Mot de passe**  
     Entrez le mot de passe utilisé avec la connexion. Cette option est disponible uniquement si vous avez sélectionné l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     **Suivant**  
     Connectez-vous au serveur et validez l'utilisateur. Ce processus vérifie si l'utilisateur dispose des autorisations répertoriées ci-dessus sur les ordinateurs sélectionnés.  
  
4.  Sur la page **Sélectionner la méthode de transfert** , sélectionnez la méthode de transfert.  
  
     **Utiliser la méthode de détachement et d'attachement**  
     Détachez la base de données du serveur source, copiez les fichiers de base de données (.mdf, .ndf et .ldf) sur le serveur de destination, puis attachez la base de données au serveur de destination. Cette méthode est généralement la plus rapide, car le travail principal consiste à lire le disque source et à écrire sur le disque de destination. Aucune logique [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est requise pour créer des objets au sein de la base de données ou pour créer des structures de stockage de données. Cependant, cette méthode peut être plus lente si la base de données contient une quantité importante d'espace alloué, mais inutilisé. Par exemple, une nouvelle base de données pratiquement vide qui est créée en allouant 100 Mo copie la totalité des 100 Mo, même si seulement 5 Mo sont utilisés.  
  
    > [!NOTE]  
    >  Cette méthode ne permet pas aux utilisateurs d'avoir accès à la base de données pendant le transfert.  
  
     **En cas d'échec, rattachez la base de données source.**  
     Lorsqu'une base de données est copiée, les fichiers de la base de données d'origine sont toujours rattachés au serveur source. Utilisez cette case pour rattacher les fichiers d'origine à la base de données source si un déplacement de base de données ne peut pas être achevé.  
  
     **Utiliser la méthode de transfert SQL Management Object**  
     Cette méthode lit la définition de chaque objet de base de données dans la base de données source et crée chaque objet dans la base de données de destination. Elle transfère ensuite les données des tables sources vers les tables de destination en recréant les index et les métadonnées.  
  
    > [!NOTE]  
    >  Les utilisateurs peuvent continuer à accéder à la base de données pendant le transfert.  
  
5.  Sur la page **Sélectionner une base de données** , sélectionnez la ou les bases de données à déplacer ou à copier du serveur source vers le serveur de destination. Consultez [limitations et restrictions](#Restrictions) dans la section « avant de Begin » de cette rubrique.  
  
     **Déplacer**  
     Déplace la base de données vers le serveur de destination.  
  
     **Copier**  
     Copie la base de données sur le serveur de destination.  
  
     **Source**  
     Permet d'afficher les bases de données existant déjà sur le serveur de destination.  
  
     **État**  
     Affiche **OK** si la base de données peut être déplacée. Sinon, indique la raison pour laquelle la base de données ne peut pas être déplacée.  
  
     **Actualisation**  
     Permet d'actualiser la liste des bases de données.  
  
     **Suivant**  
     Permet de démarrer la procédure de validation et d'accéder à l'écran suivant.  
  
6.  Sur la page **Configurer la base de données de destination** , modifiez le nom de la base de données si nécessaire et spécifiez l'emplacement et le nom des fichiers de base de données. Cette page s'affiche une seule fois, chaque fois qu'une base de données est déplacée ou copiée.  
  
7.  Sur la page **Sélectionner des objets de base de données** , sélectionnez les objets à inclure dans l'opération de déplacement ou de copie. Cette page est disponible uniquement lorsque la source et la destination correspondent à des serveurs différents. Pour inclure un objet, cliquez sur son nom dans la zone **Objets connexes disponibles** , puis cliquez sur le bouton **>>** pour déplacer l’objet vers la zone **Objets connexes sélectionnés** . Pour exclure un objet, cliquez sur le nom de l’objet dans la zone **objets connexes sélectionnés** , puis cliquez sur le **<\<** bouton pour déplacer l’objet vers la zone **objets connexes disponibles** . Par défaut, tous les objets de chaque type sélectionné sont transférés. Pour choisir des objets de tout type, cliquez sur le bouton de sélection (...) en regard d'un type d'objet dans la zone **Objets connexes sélectionnés** . Cela permet d'afficher une boîte de dialogue dans laquelle vous pouvez sélectionner des objets individuels.  
  
     **Connexions (Tou(te)s les connexions lors de l'exécution)**  
     Inclut les connexions dans l'opération de déplacement ou de copie. Option sélectionnée par défaut.  
  
     **Procédures stockées de la base de données master**  
     Inclut des procédures stockées de la base de données **master** dans l'opération de déplacement ou de copie.  
  
    > [!NOTE]  
    >  Les procédures stockées étendues et leurs DLL associées ne peuvent faire l’objet d’une copie automatique.  
  
     **travaux de l'Agent SQL Server**  
     Permet d'inclure des travaux de la base de données **msdb** dans l'opération de déplacement ou de copie.  
  
     **Messages d'erreur définis par l'utilisateur**  
     Permet d'inclure des messages d'erreur définis par l'utilisateur dans l'opération de déplacement ou de copie.  
  
     **Points de terminaison**  
     Permet d'inclure des points de terminaison définis dans la base de données source.  
  
     **Catalogue de texte intégral**  
     Permet d'inclure des catalogues de texte intégral à partir de la base de données source.  
  
     **Package SSIS**  
     Permet d'inclure des packages [!INCLUDE[ssIS](../../includes/ssis-md.md)] définis dans la base de données source.  
  
     **Description**  
     Description de l'objet .  
  
8.  Sur la page **Emplacement des fichiers de base de données sources** , spécifiez un partage de système de fichiers contenant les fichiers de base de données sur le serveur source. Ce partage est requis si les instances de serveur source et de serveur de destination se trouvent sur des ordinateurs différents.  
  
     **Sauvegarde de la base de données**  
     Affiche le nom de chaque base de données en cours de déplacement.  
  
     **Emplacement du dossier**  
     Spécifiez l'emplacement des fichiers de base de données source sur le système de fichiers.  
  
     Exemple : C:\Program Files\Microsoft SQL Server\MSSQL110.MSSQLSERVER\MSSQL\DATA  
  
     **Partage de fichier sur le serveur source**  
     Spécifiez l’emplacement des fichiers de base de données source sous la forme du chemin d'accès à un partage de fichiers.  
  
     Par exemple : « \\ \\ *SERVER_NAME*\c $ \Program Files\Microsoft SQL Server\MSSQL110. MSSQLSERVER\MSSQL\Data  
  
9. L'Assistant Copie de base de données crée un package [!INCLUDE[ssIS](../../includes/ssis-md.md)] pour transférer la base de données. Sur la page **Configurer le package** , personnalisez le package si nécessaire.  
  
     **Emplacement du package**  
     Affiche l’emplacement auquel le package [!INCLUDE[ssIS](../../includes/ssis-md.md)] sera écrit.  
  
     **Nom du package**  
     Entrez le nom du package [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
     **Options du journal**  
     Précisez si les informations du journal doivent être stockées dans le journal des événements Windows ou dans un fichier texte.  
  
     **Chemin d'accès au fichier journal des erreurs**  
     Fournissez un chemin d'accès pour l'emplacement du fichier journal. Cette option est disponible uniquement si l'option Enregistrement dans un fichier texte est sélectionnée.  
  
10. Sur la page **Planifier le package** , indiquez à quel moment vous voulez que l'opération de déplacement ou de copie commence. Si vous n'êtes pas administrateur système, vous devez spécifier un compte proxy de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui a accès au sous-système d'exécution du package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS).  
  
     **Run immediately**  
     Démarre l'opération de déplacement ou de copie une fois que vous avez appuyé sur **Suivant**.  
  
     **Planification**  
     Démarre l'opération de déplacement ou de copie plus tard. Les paramètres de planification actuels s'affichent dans la zone de description. Pour modifier la planification, cliquez sur **Modifier**.  
  
     **Changement**  
     Ouvre la boîte de dialogue **Nouvelle planification du travail** .  
  
     **Compte proxy Integration Services**  
     Sélectionnez un compte proxy disponible. Pour planifier le transfert, l'utilisateur doit avoir à sa disposition au moins un compte proxy disposant des autorisations nécessaires pour accéder au sous-système **Exécution du package SQL Server Integration Services** .  
  
     Pour créer un compte proxy pour l'exécution du package [!INCLUDE[ssIS](../../includes/ssis-md.md)] , dans l'Explorateur d'objets, développez **Agent SQL Server**puis **Proxies**, cliquez avec le bouton droit sur **Exécution du package SSIS**, puis cliquez sur **Nouveau proxy**.  
  
     Les membres du rôle serveur fixe **sysadmin** peuvent sélectionner le **Compte de service Agent SQL Server**, qui dispose des autorisations nécessaires.  
  
11. Sur la page **Terminer l'assistant** , consultez le résumé des options sélectionnées. Cliquez sur **Précédent** pour modifier une option. Cliquez sur **Terminer** pour créer la base de données. Au cours du transfert, la page **Exécution de l'opération** permet de surveiller les informations d'état relatives à l'exécution de l' **Assistant Copie de base de données**.  
  
     **Action**  
     Liste chaque action en cours de réalisation.  
  
     **État**  
     Indique si l’action a réussi ou échoué dans sa globalité.  
  
     **Message**  
     Affiche les messages retournés par chaque étape.  
  
##  <a name="follow-up-after-upgrading-a-sql-server-database"></a><a name="FollowUp"></a> Suivi : Après la mise à niveau d'une base de données SQL Server  
 Après avoir utilisé l'Assistant Copie de base de données pour mettre à niveau une base de données d'une version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], la base de données est immédiatement disponible et est automatiquement mise à niveau. Si la base de données comprend des index de recherche en texte intégral, la mise à niveau les importe, les réinitialise ou les reconstruit, selon le paramètre de la propriété de serveur **Option de mise à niveau des index de recherche en texte intégral** . Si l’option de mise à niveau a la valeur **Importer** ou **Reconstruire**, les index de recherche en texte intégral ne sont pas disponibles pendant la mise à niveau. Selon le volume de données indexé, l'importation peut prendre plusieurs heures et la reconstruction jusqu'à dix fois plus longtemps. Notez également que quand l’option de mise à niveau est **Importer**, si un catalogue de texte intégral n’est pas disponible, les index de recherche en texte intégral associés sont reconstruits. Pour plus d’informations sur l’affichage ou la modification du paramètre de la propriété **Option de mise à niveau des index de recherche en texte intégral** , consultez [Gérer et surveiller la recherche en texte intégral pour une instance de serveur](../search/manage-and-monitor-full-text-search-for-a-server-instance.md).  
  
 Si le niveau de compatibilité d'une base de données utilisateur est à 100 ou supérieur avant la mise à niveau, il reste le même après la mise à niveau. Si le niveau de compatibilité était à 90 dans la base de données mise à niveau, le niveau de compatibilité est défini à 100, ce qui correspond au niveau de compatibilité le plus bas pris en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d’informations, consultez [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).  
  
## <a name="see-also"></a>Voir aussi  
 [Mettre à niveau une base de données à l’aide du détachement et de l’attachement &#40;Transact-SQL&#41;](upgrade-a-database-using-detach-and-attach-transact-sql.md)   
 [Create a SQL Server Agent Proxy](../../ssms/agent/create-a-sql-server-agent-proxy.md)  
  
  
