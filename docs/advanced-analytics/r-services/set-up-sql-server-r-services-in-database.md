---
title: "Configurer SQL Server R Services (dans la base de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
keywords: 
  - "Installation de SQL Server R Services"
ms.assetid: 4d773c74-c779-4fc2-b1b6-ec4b4990950d
caps.latest.revision: 35
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 30
---
# Configurer SQL Server R Services (dans la base de donn&#233;es)
  Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et les versions ultérieures, vous pouvez installer tous les composants liés à [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] à l’aide de l’Assistant de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
 
 
 Une fois la configuration terminée, quelques étapes supplémentaires peuvent être requises pour activer la fonctionnalité R Services, pour configurer des comptes et pour autoriser des utilisateurs à accéder à des bases de données spécifiques.   
  
Si vous rencontrez des problèmes d’accès à la base de données après avoir terminé la configuration, ou si vous devez désinstaller les versions précédentes, consultez [FAQ d’installation et de mise à niveau &#40;SQL Server R Services&#41;](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md).  

> [!NOTE]
> Pour installer R Services (dans la base de données), le lecteur où la fonctionnalité est installée doit prendre en charge la création de noms de fichiers courts avec la notation 8dot3. Sinon, les processus qui lancent R à partir de SQL Server peuvent ne pas démarrer. Veillez à activer la notation 8dot3 sur le volume avant d’installer R Services. Cette restriction sera supprimée dans une version ultérieure.

  
##  <a name="a-namebkmkinstallrservicesindatabasea-step-1-install-r-services-in-database-on-sql-server-2016-or-later"></a><a name="bkmk_installRServicesInDatabase"></a> Étape 1 : Installer R Services (dans la base de données) sur SQL Server 2016 ou version ultérieure  
   
  
1.  Exécutez le programme d’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    Pour plus d’informations sur les installations sans assistance, consultez [Unattended Installs of SQL Server R Services](../../advanced-analytics/r-services/unattended-installs-of-sql-server-r-services.md).  
  
2.  Dans l’onglet **Installation** , cliquez sur **Nouvelle installation autonome SQL Server ou ajout de fonctionnalités à une installation existante**.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas installer [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sur un cluster de basculement. Toutefois, vous pouvez installer [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] sur un ordinateur autonome qui utilise Always On et fait partie d’un groupe de disponibilité. Pour plus d’informations sur l’utilisation de R Services dans un groupe de disponibilité Always On, consultez [Groupes de disponibilité Always On : interopérabilité](../../database-engine/availability-groups/windows/always-on-availability-groups-interoperability-sql-server.md).  
  
3.  Dans la page **Sélection de fonctionnalités** , sélectionnez les options suivantes :  
  
    -   **Services Moteur de base de données**  
  
         Au moins une instance du moteur de base de données est requise pour utiliser [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Vous pouvez utiliser l’instance par défaut ou une instance nommée.  
  
    -   **R Services (dans la base de données)**  
  
         Cette option configure les services de base de données utilisés par les travaux R et installe les extensions qui prennent en charge les scripts et processus externes.  
    > [!NOTE]
    > 
    > Si vous devez exécuter votre code R dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], veillez à installer **[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]**. 
    > 
    > En revanche, Microsoft R Server (autonome) est une option qui vous permet d’utiliser des bibliothèques ScaleR sur un ordinateur Windows qui n’exécute pas SQL Server. Nous vous suggérons d’installer Microsoft R Server (autonome) sur un ordinateur portable ou un autre ordinateur utilisé pour le développement R, pour créer des solutions R qui pourront être déployées ultérieurement sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui exécute R Services (dans la base de données).
 
  
4.  Sur la page **Consentement à l’installation de Microsoft R Open**, cliquez sur **Accepter**.  
  
     Ce contrat de licence est requis pour télécharger Microsoft R Open, qui comprend une distribution des packages de base et des outils R open source, ainsi que des packages et fournisseurs de connectivité R améliorés de Revolution Analytics.  
  
    > [!NOTE]  
    >  Si l’ordinateur que vous utilisez n’a pas accès à Internet, vous pouvez interrompre la configuration à cette étape pour télécharger les programmes d’installation séparément, comme indiqué ici : [Installation des composants R sans accès à Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md)  
  
     Cliquez sur **Accepter**, attendez que le bouton **Suivant** devienne actif, puis cliquez sur **Suivant**.  
  
5.  Sur la page **Prêt pour l’installation**, vérifiez que vos sélections sont incluses, et cliquez sur **Installer**.  
  
     **Fonctionnalités**  
  
     Services Moteur de base de données  
  
     R Services (dans la base de données)  
  
6.  Lorsque l’installation est terminée, redémarrez l’ordinateur.   
  
  
##  <a name="a-namebkmkenablefeaturea-step-2-enable-r-services-and-verify-that-local-r-script-execution-works"></a><a name="bkmk_enableFeature"></a>Étape 2 : Activer R et vérifier que l’exécution locale de script R fonctionne  
  
  
1. Ouvrez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. S’il n’est pas déjà installé, vous pouvez réexécuter l’Assistant de configuration de SQL Server pour ouvrir un lien de téléchargement et l’installer.  
  
2. Connectez-vous à l’instance où vous avez installé R Services (dans la base de données) et exécutez la commande suivante pour activer explicitement la fonctionnalité R Services ; dans le cas contraire, il ne sera pas possible d’appeler des scripts R même si la fonctionnalité a été installée par le programme.  
  
   ```    
   Exec sp_configure  'external scripts enabled', 1  
   Reconfigure  with override    
   ```  
  
10. Redémarrez le service SQL Server pour l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cette opération redémarre automatiquement le service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] . Vous pouvez redémarrer le service à l’aide du panneau Services dans le panneau de configuration ou à l’aide de SQL Server Configuration Manager.  
  
9. Une fois que le service SQL Server est disponible, vérifiez que la fonctionnalité R est activée en exécutant la commande suivante et en vérifiant que *run_value* est défini sur 1 :  
  
    ```    
    Exec sp_configure  'external scripts enabled'    
    ```  
   Vous pouvez également ouvrir le panneau **Services** et vérifier que le service Launchpad de votre instance est en cours d’exécution. Chaque instance possède son propre service Launchpad.
   
10. À présent, vous devez être en mesure d’exécuter de simples scripts R comme le suivant dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] :  
  
    ```  
    exec sp_execute_external_script  @language =N'R',  
    @script=N'OutputDataSet<-InputDataSet',    
    @input_data_1 =N'select 1 as hello'  
    with result sets (([hello] int not null));  
    go  
    ```  
  
    **Résultats**  
  
    *hello*  
    *1*   
  
> [!IMPORTANT]  Quelques étapes supplémentaires sont nécessaires si vous avez besoin d’accéder aux données de SQL Server, ou d’exécuter des commandes R à partir d’un client distant de science des données. Les étapes suivantes décrivent en détail ces critères supplémentaires.
 
  
##  <a name="a-namebkmkconfigureaccountsa-step-3-enable-implied-authentication-for-launchpad-accounts"></a><a name="bkmk_configureAccounts"></a> Étape 3 : Activer l’authentification implicite pour les comptes Launchpad  
   
  
Pendant l’installation, 20 nouveaux comptes d’utilisateur Windows sont créés pour exécuter les tâches situées dans le jeton de sécurité du service [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]. Lorsqu’un utilisateur envoie un script R depuis un client externe, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] active un compte de travail disponible, le mappe à l’identité de l’utilisateur appelant, et exécute le script R au nom de l’utilisateur. Il s’agit d’un nouveau service (appelé *authentification implicite*) du moteur de base de données qui prend en charge une exécution sécurisée des scripts externes. 

Vous pouvez afficher ces comptes dans le groupe d’utilisateurs Windows, **SQLRUserGroup**.  Si vous avez besoin d’exécuter des scripts R à partir d’un client distant de science des données et utilisez l’authentification Windows, ces comptes de travail doivent obtenir l’autorisation de se connecter à l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en votre nom.  
  
1. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l’Explorateur d’objets, développez **Sécurité**, cliquez avec le bouton droit sur **Connexions**, puis sélectionnez **Nouvelle connexion**.  
2. Dans la boîte de dialogue **Nouvelle connexion**, cliquez sur **Rechercher**.  
3. Cliquez sur **Types d’objet** et sélectionnez **Groupes**. Désélectionnez tout le reste.  
4. Dans Entrez le nom de l’objet à sélectionner, tapez *SQLRUserGroup*, et cliquez sur **Vérifier les noms**.  
5. Le nom du groupe local associé au service Launchpad de l’instance doit ressembler à quelque chose comme *nom_instance\SQLRUserGroup*. Cliquez sur **OK**.  
6. Par défaut, la connexion est affectée au rôle **public** et est autorisée à se connecter au moteur de base de données. 
7. Cliquez sur **OK**.  
  
> [!NOTE] Si vous utilisez une connexion SQL pour l’exécution de scripts R dans un contexte de calcul SQL Server, cette étape supplémentaire n’est pas requise.
  
  
## <a name="step-4-give-non-admin-users-r-script-permissions"></a>Étape 4 : Donner aux utilisateurs non administrateurs des autorisations de scripts R  
  
Si vous avez installé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vous-même et si vous exécutez des scripts R dans votre propre instance, vous exécutez généralement des scripts en tant qu’administrateur et avez donc une autorisation implicite sur différentes opérations et sur toutes les données de la base de données, ainsi que la possibilité d’installer de nouveaux packages R en fonction des besoins.  
  
Toutefois, dans un scénario d’entreprise, la plupart des utilisateurs, y compris ceux ayant accès à la base de données à l’aide de connexions SQL, ne bénéficient pas de ces autorisations élevées. Par conséquent, pour chaque utilisateur qui exécute des scripts externes, vous devez accorder des autorisations d’utilisateur pour exécuter des scripts R dans chaque base de données où R sera utilisé.   
  
  
```  
USE <database_name>  
GO  
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]  
```  

> [!TIP] Besoin d’aide pour la configuration ? Vous n’êtes pas sûr d’avoir effectué toutes les étapes ?
>
> Utilisez ces rapports personnalisés pour vérifier l’état d’installation de R Services. Pour plus d’informations, consultez [Analyser R Services à l’aide de rapports personnalisés](../../advanced-analytics/r-services/monitor-r-services-using-custom-reports-in-management-studio.md).    
  
##  <a name="a-namebkmkadditionala-optional-modifications"></a><a name="bkmk_Additional"></a> Modifications facultatives  
  
Cette section décrit les modifications supplémentaires que vous pouvez apporter à la configuration de l’instance, ou de votre client de science des données, pour prendre en charge l’exécution du script R.
  
### <a name="modify-the-number-of-worker-accounts-used-by-includersqllaunchpadtokenrsqllaunchpadmdmd"></a>Modifier le nombre de comptes de travail utilisés par [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]
  
Si vous pensez que vous utiliserez intensément R, ou que de nombreux utilisateurs exécuteront des scripts simultanément, vous pouvez augmenter le nombre de comptes de travail affectés au service Launchpad. Pour plus d’informations, voir [Modify the User Account Pool for SQL Server R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md).  
  
  
### <a name="give-your-r-users-or-logins-read-write-or-ddl-permissions-as-needed-in-additional-databases"></a>Au besoin, donnez à vos utilisateurs ou connexions R des autorisations en lecture, en écriture ou DDL dans les bases de données supplémentaires  
  
Pendant l’exécution de scripts R, le compte d’utilisateur peut avoir besoin de lire les données d’autres bases de données, de créer des tables pour stocker les résultats et d’écrire des données dans des tables. 
     
Pour chaque utilisateur qui va exécuter des scripts R, assurez-vous que le compte d’utilisateur possède les autorisations **db_datareader**, **db_datawriter**, ou **db_ddladmin** sur la base de données spécifique.   
       
Par exemple, l’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante donne à la connexion SQL *MySQLLogin* les droits nécessaires pour exécuter des requêtes T-SQL dans la base de données *RSamples*. Pour exécuter cette instruction, la connexion SQL doit déjà exister dans le contexte de sécurité du serveur.  
  
```  
USE RSamples  
GO  
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'  
```  
  
Pour plus d’informations sur les autorisations incluses dans chaque rôle, consultez [Rôles au niveau de la base de données](../../relational-databases/security/authentication-access/database-level-roles.md).  
  
  
### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>Créer une source de données ODBC pour l’instance sur votre client de science des données  
  
Si vous créez une solution R sur un ordinateur client de science des données et avez besoin de vous connecter à l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] comme contexte de calcul, vous pouvez utiliser une connexion SQL ou l’authentification Windows intégrée.  
  
Si vous utilisez une connexion SQL, vérifiez qu’elle possède les autorisations appropriées sur la base de données dans laquelle vous allez lire des données. Pour ce faire, vous pouvez ajouter les autorisations *Connect to* et *SELECT*, ou ajouter la connexion au rôle **db_datareader**. Si vous avez besoin de créer des objets, des droits **DDL_admin** sont nécessaires.  Pour enregistrer des données dans des tables, ajoutez la connexion au rôle **db_datawriter**.  
  
Si vous utilisez l’authentification Windows, vous devez configurer une source de données ODBC sur le client de science des données qui spécifie le nom de l’instance et d’autres informations de connexion.  
  
Pour plus d’informations, consultez [Utilisation de l’administrateur de sources de données ODBC](http://windows.microsoft.com/windows/using-odbc-data-source-administrator).  
  
### <a name="optimize-the-server-for-r"></a>Optimiser le serveur pour R  

Les paramètres par défaut pour la configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont destinés à optimiser l’équilibre du serveur pour un éventail de services pris en charge par le moteur de base de données, ce qui peut inclure les processus ETL, la création de rapports, l’audit et les applications qui utilisent les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par conséquent, sous les paramètres par défaut, vous pouvez trouver des ressources restreintes ou limitées pour les opérations R, en particulier dans les opérations gourmandes en mémoire.  
  
 Pour vous assurer que les tâches R sont prioritaires et correctement ressourcées, nous vous recommandons d’utiliser Resource Governor pour configurer un pool de ressources externes spécifiques à une opération R. Vous pouvez aussi modifier la quantité de mémoire allouée au moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ou augmenter le nombre de comptes s’exécutant sous le service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)].  
  
-   Configurer un pool de ressources pour gérer des ressources externes  
  
     [CREATE EXTERNAL RESOURCE POOL &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-resource-pool-transact-sql.md)  
  
-   Modifier la quantité de mémoire réservée au moteur de base de données  
  
     [Mémoire du serveur (option de configuration de serveur)](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
-   Modifier le nombre de comptes R qui peuvent être démarrés par [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]  
  
     [Modifier le pool de comptes d’utilisateurs pour SQL Server R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md)  
  
### <a name="get-the-r-source-code-optional"></a>Obtenir le code source R (facultatif)  

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] inclut une distribution des packages de base open source R.  
  
Si vous le souhaitez, cliquez sur l’un des liens suivants pour commencer immédiatement le téléchargement du code source GPL/LGPL modifié. Ce code source est mis à disposition conformément à la licence publique générale GNU, mais il n’est pas nécessaire pour installer ou utiliser [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
-   Compatible avec RC2 : télécharger l’archive [rre-gpl-src.8.0.2.tar.gz](http://go.microsoft.com/fwlink/?LinkId=786770) 
  
-   Compatible avec RC3 : télécharger l’archive [rre-gpl-src.8.0.3.tar.gz](http://go.microsoft.com/fwlink/?LinkId=786771) 

-   Compatible avec RTM : télécharger l’archive [rre-gpl-src.8.0.3.tar.gz](http://go.microsoft.com/fwlink/?LinkID=786771)
  
## <a name="troubleshooting"></a>Dépannage  
 Vous rencontrez des problèmes ? Consultez la liste des problèmes courants lors de l’installation des versions préliminaires de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]  
  
 [FAQ d’installation et de mise à niveau &#40;SQL Server R Services&#41;](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un client de science des données](../../advanced-analytics/r-services/set-up-a-data-science-client.md)   
 [Créer un serveur R autonome](../../advanced-analytics/r-services/create-a-standalone-r-server.md)  
  
  