---
title: "Installation et configuration de Master Data Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
ms.assetid: f6cd850f-b01b-491f-972c-f966b9fe4190
caps.latest.revision: 44
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 37
---
# Installation et configuration de Master Data Services
  Cet article explique comment installer [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] sur un ordinateur Windows Server 2012 R2, configurer la base de données et le site web MDS, et déployer les exemples de modèles et de données. [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) permet à votre organisation de gérer une version approuvée des données.   
   
Si vous souhaitez une vue d’ensemble de l’organisation des données dans [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)], consultez [Vue d’ensemble de Master Data Services (MDS)](../master-data-services/master-data-services-overview-mds.md).     
  
 Pour plus d’informations sur les nouvelles fonctionnalités de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)], consultez [Nouveautés de Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md).  
 
Pour obtenir des liens vers des vidéos et d’autres ressources de formation concernant [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)], consultez [En savoir plus sur Master Data Services](../master-data-services/learn-sql-server-master-data-services.md). 
  
> **Télécharger**  
>-   Pour télécharger [!INCLUDE[ssSQL15](../includes/sssql15-md.md)], accédez au  **[Centre d’évaluation](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**.  
>-   Vous avez un compte Azure ?  Cliquez **[ici](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)** pour lancer une machine virtuelle déjà équipée de [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]  .  
 
> **Vous ne parvenez pas à créer un site web MDS ?**
>>Consultez cet article du support technique Microsoft pour obtenir des instructions sur la manière de résoudre ce problème.
[Impossible de créer un site web MDS via un compte à faibles privilèges dans SQL Server 2016](https://aka.ms/mdssupport) 
  
## <a name="installing-master-data-services-and-iis-roles-and-features"></a>Installation de Master Data Services et des rôles et fonctionnalités IIS  
 Vous installez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l’aide de l’Assistant Installation du programme d’installation de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]ou d’une invite de commandes.  
  
 **Pour installer [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] à l’aide du programme d’installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur un ordinateur Windows Server 2012 R2**  
  
1.  Double-cliquez sur Setup.exe et suivez les étapes de l’Assistant Installation.  
  
2.  Dans la page [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] Sélection de fonctionnalités **, sous** Fonctionnalités partagées **, sélectionnez**.  
  
     Cette opération installe [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], des assemblys, un composant logiciel enfichable Windows PowerShell et des dossiers et fichiers pour les applications et services web.  
  
     ![mds_SQLServer2016Setup_FeatureSelection](../master-data-services/media/mds-sqlserver2016setup-featureselection.png "mds_SQLServer2016Setup_FeatureSelection")  
  
3.  Terminez l’Assistant Installation.  
  
4.  Dans [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)], cliquez sur l’icône **Gestionnaire de serveur** dans la barre des tâches sur le **Bureau**.  
  
     ![Icon for the Server Manager in Windows Server 2012 taskbar](../master-data-services/media/mds-windowsservertaskbar-servermanagericon.png "Icon for the Server Manager in Windows Server 2012 taskbar")  
  
5.  Dans le **Gestionnaire de serveur**, cliquez sur **Ajouter des rôles et fonctionnalités** dans le menu **Gérer** .  
  
     ![In Server Manage, the Add Roles and Features menu command](../master-data-services/media/mds-servermanagerdashboard-addrolesfeaturesmenu.png "In Server Manage, the Add Roles and Features menu command")  
  
6.  Dans la page **Type d’installation** de **l’Assistant Ajout de rôles et de fonctionnalités**, acceptez la valeur par défaut (**Installation basée sur un rôle ou une fonctionnalité**), puis cliquez sur **Suivant**.  
  
7.  Cliquez sur **Sélectionner un serveur du pool de serveurs**, puis cliquez sur le serveur où vous avez installé [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
     ![Server Selection page on the Add Roles and Features Wizard](../master-data-services/media/mds-servermanagerdashboard-addrolesandfeatureswizard-serverselection.png "Server Selection page on the Add Roles and Features Wizard")  
  
8.  Dans la zone **Rôles** , cliquez sur les rôles et services de rôles qui sont obligatoires pour [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] sur [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)], puis cliquez sur **Suivant**. Les images suivantes montrent les rôles et services de rôles obligatoires sélectionnés.  
  
    > [!WARNING]  
    >  N’installez pas le service de rôle Publication WebDAV. Publication WebDAV n’est pas compatible avec [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
    > [!IMPORTANT]  
    >  **Compression de contenu dynamique** est activé par défaut. Cela réduit considérablement la taille de la réponse xml et économise des E/S réseau, mais le processeur est davantage sollicité.  Pour plus d’informations, consultez **[CTP 2.0] Performances améliorées** in [What's New in Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md).  
  
    |Rôle et services de rôle|Rôle et services de rôle|  
    |-----------------------------|-----------------------------|  
    |![Common HTTP Features](../master-data-services/media/mds-servermanagerdashboard-commonhttpfeaturesroles.png "Common HTTP Features")|![Health Diagnostics Roles](../master-data-services/media/mds-servermanagerdashboard-healthdiagnosticsroles.png "Health Diagnostics Roles")|  
    |![Performance Roles](../master-data-services/media/mds-servermanagerdashboard-performanceroles.png "Performance Roles")|![Security Roles](../master-data-services/media/mds-servermanagerdashboard-securityroles.png "Security Roles")|  
    |![WebServer Application Development Roles](../master-data-services/media/mds-servermanagerdashboard-webserverapplicationdevelopmentroles.png "WebServer Application Development Roles")|![Management Tools](../master-data-services/media/mds-servermanagerdashboard-managementtoolsroles.png "Management Tools")|  
  
     Pour obtenir la liste des rôles et services de rôle obligatoires sur d’autres systèmes d’exploitation, consultez [Configuration requise pour l’application web &#40;Master Data Services&#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md).  
  
9. Dans la zone **Fonctionnalités** , cliquez sur les fonctionnalité qui sont obligatoires pour [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] sur [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)], puis cliquez sur **Suivant**. Les images suivantes montrent les fonctionnalités obligatoires sélectionnées.  
  
    |Fonctionnalités|Fonctionnalités|  
    |--------------|--------------|  
    |![Net Framework Features](../master-data-services/media/mds-servermanagerdashboard-netframeworkfeatures.png "Net Framework Features")|![Windows Process Features](../master-data-services/media/mds-servermanagerdashboard-windowsprocessfeatures.png "Windows Process Features")|  
  
     Pour obtenir la liste des fonctionnalités obligatoires sur d’autres systèmes d’exploitation, consultez [Configuration requise pour l’application web &#40;Master Data Services&#41;](../master-data-services/install-windows/web-application-requirements-master-data-services.md).  
  
 Pour plus d’informations sur l’installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l’aide du programme d’installation, consultez [Installer SQL Server 2016 avec l’Assistant Installation &#40;programme d’installation&#41;](../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md).  
  
 Pour plus d’informations sur l’installation de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l’aide d’une invite de commandes, consultez [Installer SQL Server 2016 à partir de l’invite de commandes](../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md). Lorsque vous utilisez une invite de commandes, [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] est disponible comme paramètre de fonctionnalité.  
  
 Pour obtenir une brève description des liens vers des informations supplémentaires sur les tâches de préinstallation, consultez [Installer Master Data Services](../master-data-services/install-windows/install-master-data-services.md).  
  
##  <a name="a-namesetupweba-setting-up-the-database-and-website"></a><a name="SetUpWeb"></a> Configuration de la base de données et du site web  
 **Pour configurer la base de données et le site web avec le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]**  
  
1.  Dans le volet gauche, lancez le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], puis cliquez sur **Configuration de la base de données** .  
  
2.  Dans **l’Assistant Création d’une base de données**, cliquez sur **Créer une base de données** , puis sur **Suivant**.  
  
3.  Dans la page **Serveur de base de données** , sélectionnez le **Type d’authentification** , puis cliquez sur **Tester la connexion** pour confirmer que vous pouvez vous connecter à la base de données avec les informations d’identification correspondant au type d’authentification que vous avez sélectionné.  
  
    > [!NOTE]  
    >  Si vous sélectionnez le type d’authentification **Utilisateur actuel - Sécurité intégrée** , la zone **Nom d’utilisateur** est en lecture seule et affiche le nom du compte d’utilisateur Windows qui a ouvert une session sur l’ordinateur.  
  
     ![The Database server page in the Create Database Wizard](../master-data-services/media/mds-configurationmanager-createdatabasewizard-serverpage.png "The Database server page in the Create Database Wizard")  
  
4.  Tapez un nom dans le champ **Nom de la base de données** . (Facultatif) Pour sélectionner un classement Windows et spécifier une ou plusieurs des options disponibles comme **Respecter la casse**, désactivez la case à cocher **Classement par défaut de SQL Server** .  
  
     ![The Database page in the Create Database Wizard](../master-data-services/media/mds-configurationmanager-createdatabasewizard-databasepage.png "The Database page in the Create Database Wizard")  
  
     Pour plus d’informations sur le classement Windows, consultez [Nom de classement Windows (Transact-SQL)](https://msdn.microsoft.com/library/ms188046.aspx).  
  
5.  Dans le champ **Nom d’utilisateur** , indiquez le compte Windows de l’utilisateur qui sera le Super utilisateur par défaut pour Master Data Services. Un Super utilisateur a accès à toutes les zones fonctionnelles et peut ajouter, supprimer et mettre à jour tous les modèles.  
  
     ![The Administrator Account page in the Create Database Wizard.](../master-data-services/media/mds-configurationmanager-createdatabasewizard-adminpage.png "The Administrator Account page in the Create Database Wizard.")  
  
6.  Cliquez sur **Suivant** pour afficher un récapitulatif des paramètres de la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], puis cliquez de nouveau sur **Suivant** pour créer la base de données.  
  
     Pour plus d’informations sur les paramètres de **l’Assistant Création d’une base de données**, consultez [Assistant Création d’une base de données &#40;Gestionnaire de configuration Master Data Services&#41;](../master-data-services/create-database-wizard-master-data-services-configuration-manager.md).  
  
7.  Dans la page Configuration de la base de données dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], cliquez sur Sélectionner une base de données.  
  
8.  Cliquez sur **Se connecter**, puis sélectionnez la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] que vous avez créée à l’étape 6.  
  
     ![Connect to Database dialog box for the Database Configuration page](../master-data-services/media/mds-configurationmanager-selectdatabasebutton-connecttodatabasedialog.png "Connect to Database dialog box for the Database Configuration page")  
  
     Vous avez terminé la configuration de la base de données. La page **Configuration de la base de données** affiche désormais l’instance [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à laquelle vous êtes connecté pour [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], la base de données que vous avez créée et la version actuelle de la base de données.  
  
     ![Database Configuration page in the Configuration Manager shows a completed database setup.](../master-data-services/media/mds-configurationmanager-databaseconfig-completed.png "Database Configuration page in the Configuration Manager shows a completed database setup.")  
  
9. Dans le [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], cliquez sur **Configuration web** dans le volet gauche.  
  
10. Dans la zone de liste **Site web** , cliquez sur **Site web par défaut**, puis cliquez sur **Créer** pour créer une application web.  
  
    > [!NOTE]  
    >  Lorsque vous sélectionnez **Site web par défaut**, vous devez créer une application web. Si vous sélectionnez **Créer un nouveau site web** dans la zone de liste, l’application est créée automatiquement.  
  
     ![Web Configuration page in the Configuration Manager](../master-data-services/media/mds-configurationmanager-webconfig.png "Web Configuration page in the Configuration Manager")  
  
11. Dans la section **Pool d’applications** , procédez de l’une des manières suivantes.  
  
    -   Entrez le même nom d’utilisateur que celui utilisé à l’étape 5 pour le **Compte administrateur**de la base de données,entrez le mot de passe, puis cliquez sur **OK**.  
  
         **- OU -**  
  
    -   Entrez un nom d’utilisateur différent, entrez le mot de passe, puis cliquez sur OK.  
  
         Vous n’êtes pas obligé d’utiliser le même compte lorsque vous créez la base de données et l’application web.  
  
     ![Create Web Application dialog box, Web Configuration page](../master-data-services/media/mds-configurationmanager-webconfig-createwebapplication.png "Create Web Application dialog box, Web Configuration page")  
  
     Pour plus d’informations sur la boîte de dialogue **Créer une application web**, consultez [Boîte de dialogue Créer une application web &#40;Gestionnaire de configuration Master Data Services&#41;](../master-data-services/create-web-application-dialog-box-master-data-services-configuration-manager.md).  
  
12. Dans la page **Configuration web**, dans la zone **Application web**, cliquez sur l’application que vous avez créée, puis cliquez sur **Sélectionner** dans la section **Associer l’application à la base de données**.  
  
13. Cliquez sur **Se connecter**, sélectionnez la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] que vous souhaitez associer à l’application web, puis cliquez sur **OK**.  
  
     Vous avez terminé la configuration du site web. La page **Configuration Web ** affiche maintenant le site web sélectionné, l’application web que vous avez créée et la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] associée à l’application.  
  
     ![The completed Web site configuration](../master-data-services/media/mds-configurationmanager-webconfig-completed.png "The completed Web site configuration")  
  
     Pour plus d’informations sur les paramètres de la page Configuration Web, consultez [Page Configuration Web &#40;Gestionnaire de configuration Master Data Services&#41;](../master-data-services/web-configuration-page-master-data-services-configuration-manager.md)  
  
 Vous pouvez également utiliser [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] pour spécifier d’autres paramètres pour les applications et services web associés à la base de données [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]. Par exemple, vous pouvez spécifier la fréquence à laquelle les données sont chargées ou des e-mails de validation envoyés. Pour plus d’informations, consultez [System Settings &#40;Master Data Services&#41;](../master-data-services/system-settings-master-data-services.md) (Paramètres système &#40;Master Data Services&#41;).  
  
##  <a name="a-namedeploysamplea-deploying-sample-models-and-data"></a><a name="deploySample"></a> Déploiement des exemples de modèles et de données  
 Les trois packages d’exemples de modèles suivants sont inclus avec  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].   Ces exemples de modèles incluent des données. **L’emplacement par défaut de ces packages est %programfiles%\Microsoft SQL Server\130\Master Data Services\Samples\Packages.**
  
-   chartofaccounts_en.pkg  
  
-   customer_en.pkg  
  
-   product_en.pkg  
  
 Déployez ces packages à l’aide de l’outil MDSModelDeploy. L’emplacement par défaut de l’outil MDSModelDeploy est *lecteur*\Program Files\Microsoft SQL Server\ 130\Master Data Services\Configuration.  
  
 Pour plus d’informations sur la configuration requise pour l’exécution de cet outil, consultez [Déployer un package de déploiement de modèle à l’aide de MDSModelDeploy](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md).  
  
 Pour plus d’informations sur les mises à jour des données visant à assurer la prise en charge des nouvelles fonctionnalités dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], consultez [Exemples : packages de déploiement de modèles &#40;Master Data Services&#41;](../Topic/Samples:%20Model%20Deployment%20Packages%20\(Master%20Data%20Services\).md).  
  
 **Pour déployer les exemples de modèles**  
  
1.  Copiez les packages d’exemples de modèles dans *lecteur*\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration.  
  
2.  Ouvrez une invite de commandes d’administrateur et accédez à MDSModelDeploy.exe en exécutant la commande suivante.  
  
    ```  
    cd c:\Program Files\Microsoft SQL Server\130\Master Data Services\Configuration  
    ```  
  
3.  Déployez chacun des exemples de modèles sur [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] en exécutant les commandes suivantes.  
  
    > [!IMPORTANT]  
    >  Dans les exemples ci-dessous, la valeur de service `MDS1` est spécifiée. Vous utilisez cette valeur si vous avez sélectionné  **Site Web par défaut** lors de la configuration du site web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  Consultez la section [Configuration de la base de données et du site web](#SetUpWeb) .  
    >   
    >  Si vous avez créé un site web ou sélectionné un autre site web existant, commencez par exécuter la commande suivante afin de déterminer la valeur de service correcte.  
    >   
    >  `MDSModelDeploy listservices`  
    >   
    >  La première valeur de service dans la liste des valeurs renvoyées est celle que vous avez spécifiée pour déployer un modèle.  
  
     **Pour déployer l’exemple de modèle chartofaccounts_en.pkg**  
  
    ```  
    MDSModelDeploy deploynew -package chartofaccounts_en.pkg -model ChartofAccounts -service MDS1  
    ```  
  
     **Pour déployer l’exemple de modèle customer_en.pkg**  
  
    ```  
    MDSModelDeploy deploynew -package customer_en.pkg -model Customer -service MDS1  
    ```  
  
     **Pour déployer l’exemple de modèle product_en.pkg**  
  
    ```  
    MDSModelDeploy deploynew -package product_en.pkg -model Product -service MDS1  
  
    ```  
  
     Lorsqu’un modèle est déployé avec succès, le message **Opération MDSModelDeploy terminée** s’affiche.  
  
     L’image suivante montre la commande de déploiement de l’exemple de modèle product_en.pkg.  
  
     ![Command line for deploying the Product sample model](../master-data-services/media/mds-commandprompt-deployingsamplemodel-product.png "Command line for deploying the Product sample model")  
  
4.  Pour afficher les exemples de modèles, procédez comme suit.  
  
    1.  Accédez au site web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] que vous avez configuré. Consultez la section [Configuration de la base de données et du site web](#SetUpWeb) .  
  
         L’adresse du site web est http://*nom du serveur*/*application web*/.  
  
    2.  Sélectionnez un modèle dans la zone de liste **Modèle** , puis cliquez sur **Explorer**.  
  
         ![MDS Web site, home page.](../master-data-services/media/mds-mdswebsite-homepage-selectsamplemodel.png "MDS Web site, home page.")  
  
## <a name="next-step"></a>Étape suivante  
 Créer un nouveau modèle et les entités pour vos données. Consultez [Créer un modèle &#40;Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md) et [Créer une entité &#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md).  
  
 Pour obtenir une vue d’ensemble sur l’utilisation d’un modèle et d’entités en vue de créer une structure pour vos données dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], consultez [Vue d’ensemble de Master Data Services &#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md).  
  
## <a name="did-this-article-help-you-were-listening"></a>Cet article vous a-t-il été utile ? Nous sommes à votre écoute  
 Quels renseignements souhaitez-vous obtenir ? Avez-vous trouvé ce que vous cherchiez ? Nous tenons compte de vos commentaires pour améliorer le contenu de nos articles. Veuillez envoyer vos commentaires à [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Get%20Started%20with%20Master%20Data%20Services)  
  
## <a name="see-also"></a>Voir aussi  
 [Base de données Master Data Services](../master-data-services/master-data-services-database.md)   
 [Application web Master Data Manager](../master-data-services/master-data-manager-web-application.md)   
 [Page Configuration de base de données &#40;Gestionnaire de configuration Master Data Services&#41;](../master-data-services/database-configuration-page-master-data-services-configuration-manager.md)   
 [Nouveautés de Master Data Services &#40;MDS&#41;](../master-data-services/what-s-new-in-master-data-services-mds.md)  
  
  