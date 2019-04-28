---
title: Déployer une base de données SQL Server sur une machine virtuelle Microsoft Azure | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.deploymentwizard.deploymentsettings.f1
- sql12.swb.deploymentwizard.progress.f1
- sql11.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.f1
- sql12.swb.deploymentwizard.azuresignin.f1
- sql11.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.azuresignin.f1
- sql12.swb.deploymentwizard.f1
- sql12.swb.sqlvmdialog.f1
- sql11.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.results.f1
- sql11.swb.deploymentwizard.progress.f1
- sql12.swb.newvmdialog.f1
- sql12.swb.deploymentwizard.sourcesettings.f1
- sql12.swb.usevmdialog.f1
- sql11.swb.deploymentwizard.sourcesettings.f1
- sql11.swb.deploymentwizard.results.f1
- sql12.swb.deploymentwizard.summary.f1
- sql11.swb.deploymentwizard.deploymentsettings.f1
helpviewer_keywords:
- Deploy a database
- Deploy to Azure VM
- Migrate to Azure
- Windows Azure virtual machine
- Migrate to Azure VM
- Migrate to the cloud
- SQL Server Management Studio
- SSMS
- Deploy database wizard
- Deploy a SQL Server database to Azure
- Azure VM
ms.assetid: 5e82e66a-262e-4d4f-aa89-39cb62696d06
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 40f1bf8c37ab27bc00fd291d6687737215519259
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62871678"
---
# <a name="deploy-a-sql-server-database-to-a-microsoft-azure-virtual-machine"></a>Déployer une base de données SQL Server sur une machine virtuelle Microsoft Azure
  Utilisez l’Assistant **Déployer une base de données SQL Server sur une machine virtuelle Windows Azure** pour déployer une base de données d’une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans une machine virtuelle Windows Azure (VM). L'Assistant utilise une sauvegarde complète de la base de données ; par conséquent, il copie toujours le schéma complet de la base de données et les données d'une base de données utilisateur SQL Server. L'Assistant effectue également toutes les configurations de machine virtuelle Windows Azure pour vous ; par conséquent, aucune configuration préalable de machine virtuelle n'est requise.  
  
 Vous ne pouvez pas utiliser l'Assistant pour les sauvegardes différentielles, car il ne remplace pas une base de données existante portant le même nom de base de données. Pour remplacer une base de données existante sur la machine virtuelle, vous devez d'abord supprimer la base de données existante ou modifier le nom de la base de données. S'il existe un conflit de noms entre le nom de la base de données d'une opération de déploiement en cours et d'une base de données existante sur la machine virtuelle, l'Assistant suggère un nom de base de données avec suffixe pour la base de données en cours pour vous permettre d'effectuer cette opération.  
  
##  <a name="before_you_begin"></a> Avant de commencer  
 Pour exécuter cet Assistant, vous devez être en mesure de fournir les informations suivantes et avoir défini ces paramètres de configuration :  
  
-   Informations de compte Microsoft associées à l'abonnement Windows Azure.  
  
-   Votre profil de publication Windows Azure.  
  
    > [!CAUTION]  
    >  SQL Server prend actuellement en charge la version 2.0 du profil de publication. Pour télécharger la version prise en charge du profil de publication, consultez [Télécharger le profil de publication 2.0](https://go.microsoft.com/fwlink/?LinkId=396421).  
  
-   Certificat de gestion téléchargé dans votre abonnement Windows Azure.  
  
-   Certificat de gestion enregistré dans le magasin de certificats personnel de l'ordinateur local sur lequel l'Assistant s'exécute.  
  
-   Vous devez disposer d'un emplacement de stockage temporaire disponible sur l'ordinateur sur lequel la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est hébergée. L'emplacement de stockage temporaire doit également être disponible sur l'ordinateur sur lequel s'exécute l'Assistant.  
  
-   Si vous déployez la base de données sur un ordinateur virtuel existant, l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être configurée pour écouter sur un port TCP/IP.  
  
-   L'image de machine virtuelle Windows Azure ou de galerie que vous prévoyez d'utiliser pour créer la machine virtuelle doit disposer de l'adaptateur de cloud SQL Server configuré et en cours d'exécution.  
  
-   Vous devez configurer un point de terminaison ouvert pour votre adaptateur de cloud SQL Server sur la passerelle Windows Azure avec le port privé 11435.  
  
 De plus, si vous projetez de déployer votre base de données dans un ordinateur virtuel Windows Azure existant, vous devez également fournir :  
  
-   Nom DNS du service de cloud computing qui héberge votre ordinateur virtuel.  
  
-   Informations d'identification de l'administrateur pour l'ordinateur virtuel.  
  
-   Informations d'identifications avec privilèges d'opérateur Backup sur la base de données que vous prévoyez de déployer, à partir de l'instance source de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Pour plus d’informations sur l’exécution de SQL Server dans les machines virtuelles Windows Azure, consultez [se préparer à migrer vers SQL Server dans les Machines virtuelles Windows Azure](https://msdn.microsoft.com/library/dn133142.aspx).  
  
 Sur les ordinateurs qui exécutent des systèmes d'exploitation Windows Server, vous devez utiliser les paramètres de configuration suivants pour exécuter l'Assistant :  
  
-   Désactiver la Configuration de sécurité renforcée :  Utilisez le Gestionnaire de serveur > serveur Local pour définir la Configuration de sécurité renforcée d’Internet Explorer (ESC) **OFF**.  
  
-   Activez JavaScript :  Internet Explorer > Options Internet > sécurité > niveau client > Scripts > Active Scripting : **Activer**.  
  
###  <a name="limitations"></a> Limitations et restrictions  
 La limite de taille de la base de données pour cette opération est 1 To.  
  
 Ce déploiement est disponible dans SQL Server Management Studio pour [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
 Cette fonctionnalité de déploiement sert uniquement avec les bases de données utilisateur ; le déploiement de bases de données système n'est pas pris en charge.  
  
 La fonctionnalité de déploiement ne prend pas en charge les services hébergés qui sont associés à un groupe d'affinités. Par exemple, les comptes de stockage associés à un groupe d'affinités ne peuvent pas être sélectionnés pour être utilisés sur la page **Paramètres de déploiement** de cet Assistant.  
  
 La version de SQL Server dans la machine virtuelle doit être identique ou ultérieure à la version de SQL Server source. Versions de la base de données SQL Server qui peuvent être déployées sur une machine virtuelle Windows Azure à l'aide de cet Assistant :  
  
-   SQL Server 2008  
  
-   SQL Server 2008 R2  
  
-   SQL Server 2012  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 Les versions de base de données SQL Server exécutées dans une machine virtuelle Windows Azure peuvent être déployées dans :  
  
-   SQL Server 2012  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 S'il existe un conflit de noms entre le nom de la base de données d'une opération de déploiement en cours et d'une base de données existante sur la machine virtuelle, l'Assistant suggère un nom de base de données avec suffixe pour la base de données en cours pour vous permettre d'effectuer cette opération.  
  
###  <a name="filestream"></a> Éléments à prendre en considération pour déployer une base de données FILESTREAM sur des machines virtuelles Windows Azure  
 Tenez compte des instructions et des restrictions suivantes lorsque vous déployez des bases de données possédant des objets blob stockés dans des objets FILESTREAM :  
  
-   La fonctionnalité de déploiement ne peut pas déployer une base de données FILESTREAM dans de nouvelles machines virtuelles. Si FILESTREAM n'est pas activé dans la machine virtuelle avant d'exécuter l'Assistant, l'opération de restauration de base de données échouera et l'Assistant ne pourra pas achever l'opération. Pour déployer correctement une base de données qui utilise FILESTREAM, activez FILESTREAM dans l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur la machine virtuelle hôte avant de lancer l'Assistant. Pour plus d’informations, consultez [FILESTREAM (SQL Server)](https://msdn.microsoft.com/library/gg471497.aspx).  
  
-   Si votre base de données utilise l'OLTP en mémoire, déployez la base de données sur une machine virtuelle Azure sans aucune modification à la base de données. Pour plus d’informations, consultez [OLTP en mémoire (optimisation en mémoire)](https://msdn.microsoft.com/library/dn133186\(SQL.120\).aspx).  
  
###  <a name="geography"></a> Éléments à prendre en considération pour la répartition géographique des actifs  
 Notez que les actifs suivants doivent se trouver dans la même région géographique :  
  
-   Service de cloud computing  
  
-   Emplacement de la machine virtuelle  
  
-   Service de stockage de disque de données  
  
 Si les actifs répertoriés ci-dessus ne sont pas colocalisés, l'Assistant ne pourra pas terminer l'opération.  
  
###  <a name="configuration_settings"></a> Assistant Paramètres de configuration  
 Utilisez les informations de configuration suivantes pour modifier les paramètres d'un déploiement de base de données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une machine virtuelle Azure.  
  
-   **Chemin par défaut du fichier de configuration** - %LOCALAPPDATA%\SQL Server\Deploy to SQL in WA VM\DeploymentSettings.xml  
  
-   **Structure du fichier de configuration**  
  
    -   \<DeploymentSettings>  
  
        -   <OtherSettings  
  
            -   TraceLevel="Debug" \<!-- Logging level -->  
  
            -   BackupPath="\\\\[server name]\\[volume]\\" \<!-- The last used path for backup. Utilisé comme valeur par défaut dans l'Assistant. -->  
  
            -   CleanupDisabled = False /> \<!-- L’Assistant ne supprimera pas les fichiers intermédiaires et les objets Windows Azure (VM, CS, SA). -->  
  
        -   <PublishProfile \<! -- Dernières informations de profil de publication utilisées. -->  
  
            -   Certificate="12A34B567890123ABCD4EF567A8" \<!-- Certificat à utiliser dans l’Assistant. -->  
  
            -   Subscription="1a2b34c5-67d8-90ef-ab12-xxxxxxxxxxxxx" \<!-- Abonnement à utiliser dans l’Assistant. -->  
  
            -   Name="My Subscription" \<!-- Nom de l’abonnement. -->  
  
            -   Publisher="" />  
  
    -   \</DeploymentSettings>  
  
 **Valeurs du fichier de configuration**  
  
###  <a name="permissions"></a> Autorisations  
 La base de données déployée doit avoir un état normal, doit être accessible au compte d'utilisateur qui exécute l'Assistant, et le compte d'utilisateur doit avoir les autorisations requises pour exécuter une opération de sauvegarde.  
  
##  <a name="launch_wizard"></a> À l’aide de la base de données de déployer Windows Azure VM Assistant  
 **Pour lancer l'Assistant, suivez les étapes suivantes :**  
  
1.  Utilisez SQL Server Management Studio pour vous connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec la base de données que vous souhaitez déployer.  
  
2.  Dans l' **Explorateur d'objets**, développez le nom de l'instance, puis développez le nœud **Bases de données** .  
  
3.  Avec le bouton droit de la base de données que vous souhaitez déployer, sélectionnez **tâches**, puis sélectionnez **déployer la base de données à la machine virtuelle Windows Azure...**  
  

  
##  <a name="Introduction"></a> Page Introduction  
 Cette page décrit l'Assistant **Déploiement d'une base de données SQL Server dans une machine virtuelle Windows Azure** .  
  
 **Options**  
  
-   **Ne plus afficher cette page.** - Cochez cette case pour ne plus afficher la page Introduction à l'avenir.  
  
-   **Suivant** – Passe à la page **Paramètres de la source**.  
  
-   **Annuler** : annule l’opération et ferme l’Assistant.  
  
-   **Aide** -lance la rubrique d’aide MSDN pour l’Assistant.  
  
##  <a name="Source_settings"></a> Paramètres de la source  
 Utilisez cette page pour vous connecter à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge la base de données que vous souhaitez déployer dans l'ordinateur virtuel Windows Azure. Spécifiez également un emplacement temporaire pour les fichiers que vous stockez sur l'ordinateur local avant de les transférer vers Windows Azure. Il peut s'agir d'un emplacement réseau partagé.  
  
 **Options**  
  
-   Cliquez sur **connecter...**  et spécifiez les informations de connexion pour l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge la base de données à déployer.  
  
-   Utilisez la liste déroulante **Sélectionner une base de données** pour spécifier la base de données à déployer.  
  
-   Dans le champ **Autres paramètres** , spécifiez un dossier partagé qui sera accessible au service d'ordinateur virtuel Windows Azure.  
  
##  <a name="Azure_sign-in"></a> Windows authentification dans Azure  
 Utilisez cette page pour vous connecter à Windows Azure et fournir le certificat de gestion ou publier des informations de profil.  
  
 **Options**  
  
-   **Certificat de gestion** -Utilisez cette option pour spécifier un certificat dans le magasin de certificats local qui correspond au certificat de gestion de Windows Azure.  
  
-   **Profil de publication** -Utilisez cette option si vous disposez déjà d’un profil de publication téléchargé sur votre ordinateur.  
  
-   **Se connecter** - Utilisez cette option pour vous connecter à Windows Azure à l’aide d’un Microsoft compte - par exemple, un Live ID ou un compte Hotmail - pour générer et télécharger un nouveau certificat de gestion. Notez que le nombre de certificats par abonnement est limité.  
  
-   **Abonnement** - sélectionner, tapez ou collez votre ID d’abonnement Windows Azure qui correspond au certificat de gestion dans le magasin de certificats local ou un profil de publication.  
  
##  <a name="Deployment_settings"></a> Page Paramètres de déploiement  
 Utilisez cette page pour spécifier le serveur de destination et fournir des détails sur votre nouvelle base de données.  
  
 **Options**  
  
-   **Machine virtuelle** -spécifier les détails de la machine virtuelle qui hébergera la base de données SQL Server :  
  
-   **Nom du Service cloud** -spécifiez le nom du service qui héberge la machine virtuelle. Pour créer un service de cloud computing, spécifiez un nom.  
  
-   **Nom de Machine virtuelle** -spécifiez le nom de la machine virtuelle qui hébergera la base de données SQL Server. Pour créer une machine virtuelle Windows Azure, spécifiez un nom.  
  
-   **Paramètres** -utilisez le bouton Paramètres pour créer une machine virtuelle pour héberger la base de données SQL Server. Si vous utilisez une machine virtuelle existante, les informations spécifiées seront utilisées pour authentifier vos informations d'identification.  
  
-   **Compte de stockage** -sélectionnez le compte de stockage dans la liste déroulante. Pour créer un compte de stockage, spécifiez un nom. Notez que les comptes de stockage associés à un groupe d'affinités ne seront pas disponibles dans la liste déroulante.  
  
-   **Base de données cible** -spécifier les détails de la base de données cible.  
  
-   **Connexion au serveur** -détails de connexion pour le serveur.  
  
-   **Base de données** : spécifiez ou confirmez le nom d’une base de données. Si le nom de la base de données existe déjà sur l'instance SQL Server de destination, modifiez le nom.  
  
##  <a name="Summary"></a> Page Résumé  
 Utilisez cette page pour passer en revue les paramètres spécifiés pour l'opération. Pour terminer le déploiement à l'aide des paramètres spécifiés, cliquez sur **Terminer**. Pour annuler le déploiement et quitter l'Assistant, cliquez sur **Annuler**.  
  
 Des étapes manuelles peuvent être nécessaires pour déployer les détails de la base de données sur la base de données SQL Server dans un ordinateur virtuel Windows Azure. Ces étapes seront décrites de façon détaillée.  
  
##  <a name="Results"></a> Page Résultats  
 Cette page signale la réussite ou l'échec de l'opération de déploiement, affichant les résultats de chaque action. Toute action pour laquelle une erreur s'est produite comportera une indication dans la colonne **Résultat** . Cliquez sur le lien pour consulter le rapport d'erreur de cette action.  
  
 Cliquez sur **Terminer** pour fermer l'Assistant.  
  
## <a name="see-also"></a>Voir aussi  
 [L’adaptateur de cloud pour SQL Server](../../database-engine/cloud-adapter-for-sql-server.md)   
 [Gestion du cycle de vie de base de données](../database-lifecycle-management.md)   
 [Exporter une application de la couche Données](../data-tier-applications/export-a-data-tier-application.md)   
 [Importer un fichier BACPAC pour créer une nouvelle base de données utilisateur](../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md)   
 [Sauvegarde et restauration Base de données SQL Azure](https://msdn.microsoft.com/library/azure/jj650016.aspx)   
 [Déploiement de SQL Server dans Windows Azure Virtual Machines](https://msdn.microsoft.com/library/dn133141.aspx)   
 [Préparation à la migration vers SQL Server dans Windows Azure Virtual Machines](https://msdn.microsoft.com/library/dn133142.aspx)  
  
  
