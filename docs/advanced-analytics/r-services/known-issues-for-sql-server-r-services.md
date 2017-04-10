---
title: "Probl&#232;mes connus pour les Services SQL Server R | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b37a63a-5ff5-478e-bcc2-d13da3ac241c
caps.latest.revision: 52
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 49
---
# Probl&#232;mes connus pour les Services SQL Server R
  Cette rubrique décrit les limitations et problèmes de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] et de ses composants associés dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)].  
  
> [!NOTE]
> Les autres problèmes liés à l’installation initiale et à la configuration sont répertoriés ici : [ FAQ d’installation et de mise à niveau](../../advanced-analytics/r-services/upgrade-and-installation-faq-sql-server-r-services.md).  
  
## <a name="r-services-in-database"></a>R Services (dans la base de données)  
 Cette section répertorie les problèmes spécifiques à la fonctionnalité du moteur de base de données qui prend en charge l’intégration de R.  

### <a name="install-latest-service-release-to-ensure-compatibility-with-microsoft-r-client"></a>Installer la dernière version de service pour garantir la compatibilité avec Microsoft R Client

Si vous installez la dernière version de Microsoft R Client et l’utilisez pour exécuter R sur SQL Server à l’aide d’un contexte de calcul distant, il est possible que vous obteniez l’erreur suivante :

*Vous exécutez la version 9.0.0 de Microsoft R Client sur votre ordinateur, ce qui est incompatible avec la version 8.0.3 de Microsoft R Server. Téléchargez et installez une version compatible.*

En règle générale, la version de R installée avec SQL Server R Services est mise à jour lors de la publication des versions de service. Pour vous assurer que vous disposez toujours des versions les plus récentes des composants R, installez tous les Service Packs. Pour la compatibilité avec Microsoft R Client 9.0.0, vous devez installer les mises à jour qui sont décrites dans cet [article de support](https://support.microsoft.com/kb/3210262). 
  
### <a name="new-license-agreement-for-r-components-required-for-unattended-installs"></a>Nouveau contrat de licence pour les composants R requis pour les installations sans assistance  
 Si vous utilisez la ligne de commande pour installer une instance de SQL Server sur laquelle [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] est déjà installé, vous devez modifier la ligne de commande pour utiliser le nouveau paramètre de contrat de licence, */IACCEPTROPENLICENSEAGREEMENT*. Si vous n’utilisez pas l’argument approprié, la configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] risque d’échouer.  
  
### <a name="warning-of-incompatible-version-when-connecting-to-older-version-of-sql-server--r-services-from-a-client-using-includesssqlv14mdtokensqlv14sssqlv14mdmd"></a>Avertissement de version incompatible lors de la connexion à une version antérieure de SQL Server R Services à partir d’un client à l’aide de [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] 

Si vous avez installé Microsoft R Server sur un ordinateur client à l’aide de l’Assistant de configuration de [!INCLUDE[ssSQLv14_md](../../includes/sssqlv14-md.md)] ou le nouveau programme d’installation autonome pour [Microsoft R Server](https://msdn.microsoft.com/microsoft-r/rserver-install-windows), et que vous exécutez le code R dans un contexte de calcul qui utilise une version antérieure de SQL Server Services R, il est possible que vous obteniez une erreur semblable à la suivante :

*Vous exécutez la version 9.0.0 de Microsoft R Client sur votre ordinateur, ce qui est incompatible avec la version 8.0.3 de Microsoft R Server. Téléchargez et installez une version compatible.*

L’outil **SqlBindR.exe** est fourni dans la version Microsoft R Server 9.0 pour prendre en charge la mise à niveau des instances de SQL Server vers une version compatible 9.0. La prise en charge de la mise à niveau des instances de R Services vers 9.0 va être ajoutée à SQL Server dans le cadre de la version de service à venir. Les versions candidates pour la mise à niveau future incluent SQL Server 2016 RTM CU3+ et SP1+, ainsi que SQL Server vNext CTP 1.1. 

### <a name="setup-for-sql-server-2016-service-releases-might-fail-to-install-newer-versions-of-r-components"></a>La configuration des versions de services de SQL Server 2016 peut échouer à installer de nouvelles versions des composants R

Lorsque vous installez une mise à jour cumulative ou un Service Pack pour SQL Server 2016 sur un ordinateur qui n’est pas connecté à Internet, l’Assistant de configuration peut échouer à afficher l’invite qui vous permet de mettre à jour les composants R à l’aide des fichiers CAB téléchargés. Cela se produit généralement lorsque plusieurs composants sont installés avec le moteur de base de données.
 
Pour résoudre ce problème, vous pouvez installer la version de service à l’aide de la ligne de commande et spécifier l’argument /MRCACHEDIRECTORY, comme indiqué dans cet exemple pour CU1 : 

`C:\<path to installation media>\SQLServer2016-KB3164674-x64.exe /Action=Patch /IACCEPTROPENLICENSETERMS /MRCACHEDIRECTORY=<path to CU1 CAB files>`

Pour obtenir les derniers fichiers CAB, consultez [Installation des composants R sans accès à Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md).

### <a name="windows-group-created-for-launchpad-must-have-an-account-in-the-sql-server-instance"></a>Le groupe Windows créé pour LaunchPad doit posséder un compte dans l’instance SQL Server
 Lors de l’installation de SQL Server R Services, un groupe d’utilisateurs Windows est créé avec le nom par défaut **SQLRUsers** utilisé par le Launchpad approuvé pour exécuter les tâches R. Si vous avez besoin d’exécuter des tâches R à partir d’un client distant à l’aide de l’authentification intégrée Windows, vous devez autoriser ce groupe d’utilisateurs Windows à vous connecter à l’instance SQL Server où R est activé.

Dans un environnement dans lequel **SQLRUsers** n’a pas cette autorisation, vous pouvez rencontrer les erreurs suivantes :  
  
-   Quand vous tentez d’exécuter des scripts R :  
  
     *Impossible de lancer le runtime pour le script « R ». Vérifiez la configuration du runtime « R ».*  
  
     *Une erreur de script externe s’est produite. Impossible de lancer le runtime.*  
  
-   Erreurs générées par le service [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] :  
  
     *Impossible d’initialiser le lanceur RLauncher.dll*  
  
     *Aucune DLL de lanceur n’a été enregistrée.*  
  
-   Les journaux de sécurité indiquent que le compte NT SERVICE\MSSQLLAUNCHPAD n’a pas pu se connecter.  
 
> [!NOTE]
> Si vous exécutez des tâches R dans SQL Server Management Studio à l’aide de la mémoire partagée, il est possible que vous ne rencontriez pas cette limitation jusqu’à ce que votre tâche R utilise un appel ODBC incorporé. 
> 
> Cette solution de contournement n’est pas nécessaire si vous utilisez des connexions SQL à partir de la station de travail distante.

### <a name="launchpad-services-fails-to-start-if-version-is-different-than-r-version"></a>Le service LaunchPad ne parvient pas à démarrer si la version est différente de la version de R
Si vous installez R Services séparément à partir du moteur de base de données et que les versions sont différentes, il est possible que cette erreur s’affiche dans le journal des événements système : _Le service Launchpad SQL Server a échoué à démarrer en raison de l’erreur suivante : « Le service n’a pas répondu assez vite à la demande de lancement ou de contrôle. »_

Par exemple, cette erreur peut se produire si vous installez le moteur de base de données à l’aide de la version, appliquez un correctif pour mettre à niveau le moteur de base de données, puis ajoutez R Services à l’aide de la version.

Pour éviter ce problème, assurez-vous que tous les composants ont le même numéro de version. Si vous mettez à niveau un composant, veillez à appliquer la même mise à niveau à tous les autres composants installés.

Pour afficher une liste des numéros de version R requis pour chaque version de SQL Server 2016, consultez [Installation des composants R sans accès à Internet](../../advanced-analytics/r-services/installing-r-components-without-internet-access.md).


### <a name="service-account-for-launchpad-requires-permission-replace-process-level-token"></a>Le compte de service pour LaunchPad nécessite l’autorisation de remplacement d’un jeton de niveau processus
 Sur l’installation de SQL Server Services R, le Launchpad approuvé est démarré à l’aide du compte NT Service\MSSQLLaunchpad, qui par défaut est configuré avec les autorisations nécessaires. Toutefois, si vous utilisez un autre compte ou modifiez les privilèges associés à ce compte, le démarrage du Launchpad peut échouer.
 
 Pour garantir que le compte de service Launchpad peut se connecter, accordez au compte le privilège : `Replace Process Level Token`. Pour plus d’informations, consultez [Remplacer un jeton de niveau processus](https://technet.microsoft.com/itpro/windows/keep-secure/replace-a-process-level-token).

### <a name="remote-compute-contexts-blocked-by-firewall-in-sql-server-instances-running-on-azure-virtual-machines"></a>Contextes de calcul distant bloqués par le pare-feu dans les instances de SQL Server s’exécutant sur des machines virtuelles  
 Si vous avez installé [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] sur une machine virtuelle Microsoft Azure, vous risquez de ne pas pouvoir utiliser les contextes de calcul qui exigent l’utilisation de l’espace de travail de la machine virtuelle. Cela est dû au fait que, par défaut, le pare-feu de la machine virtuelle Azure comprend une règle qui bloque l’accès réseau pour les comptes d’utilisateur R locaux.  
  
 Pour résoudre ce problème, sur la machine virtuelle Azure, ouvrez **Pare-feu Windows avec fonctions avancées de sécurité**, sélectionnez **Règles de trafic sortant**, et désactivez la règle suivante : « Block network access for R local user accounts in SQL Server instance MSSQLSERVER » (« Bloquer l’accès au réseau pour les comptes d’utilisateur locaux R dans l’instance SQL Server MSSQLSERVER »).  
  
### <a name="implied-authentication-in-sqlexpress"></a>Authentification implicite dans SQLEXPRESS
Lorsque vous exécutez les tâches R à partir d’une station de travail de science des données distantes à l’aide de l’authentification intégrée Windows, SQL Server utilise *l’authentification implicite* pour générer tous les appels ODBC locaux qui peuvent être requis par le script. Toutefois, cette fonctionnalité ne marchait pas dans la version RTM de SQL Server Express Edition. 

Pour résoudre ce problème, nous vous recommandons d’effectuer la mise à niveau vers une version ultérieure du service.

Si vous ne pouvez pas effectuer la mise à niveau, vous pouvez utiliser une connexion SQL pour exécuter des tâches R à distance qui peuvent nécessiter des appels ODBC incorporés. 

### <a name="limitations-on-processor-affinity-for-r-jobs"></a>Limitations sur l’affinité du processeur pour les tâches R 
 
Dans la version RTM de SQL Server 2016, vous pouvez définir l’affinité du processeur uniquement pour les processeurs dans le premier groupe de processeurs (K-Group). Par exemple, si le serveur est une machine à 2 sockets avec 2 K-Groups, seuls les processeurs du premier K-Group sont utilisés pour les processus R. La même restriction s’applique lors de la configuration de la gouvernance des ressources pour les tâches de script R.

Ce problème est résolu dans le Service Pack 1 de SQL Server 2016.

### <a name="changes-to-column-types-cannot-be-performed-when-reading-data-in-a-sql-server-compute-context"></a>Les modifications des types de colonne ne peuvent pas être effectuées lors de la lecture de données dans un contexte de calcul SQL Server

Si votre contexte de calcul est défini sur l’instance SQL Server, vous ne pouvez pas utiliser l’argument _colClasses_ (ou d’autres arguments similaires) pour modifier le type de données des colonnes dans votre code R. 

Par exemple, l’instruction suivante génère une erreur si la colonne CRSDepTimeStr n’est pas déjà un entier :

~~~~
data <- RxSqlServerData(sqlQuery = "SELECT CRSDepTimeStr, ArrDelay  FROM AirlineDemoSmall",
                                connectionString = connectionString,
                                colClasses = c(CRSDepTimeStr = "integer"))
~~~~

Ce problème sera résolu dans une version ultérieure. 

Pour résoudre ce problème, vous pouvez réécrire la requête SQL pour utiliser CAST ou CONVERT, et présenter les données à R avec le type de données approprié. En général, il vaut mieux que les performances fonctionnent avec des données à l’aide de SQL plutôt que de modifier les données dans le code R.
  
### <a name="resource-governance-default-values"></a>Valeurs par défaut de la gouvernance des ressources  
Dans Enterprise Edition, vous pouvez utiliser des pools de ressources pour gérer les processus de script externe. Dans certaines versions, la mémoire maximum pouvant être allouée aux processus R était de 20 %. Par conséquent, si le serveur possédait 32 Go de RAM, les fichiers exécutables R (RTerm.exe et BxlServer.exe) pouvaient utiliser 6.4 Go maximum dans une seule requête. 

Si vous faites face à des limitations de ressource, vérifiez la valeur par défaut appliquée. Si une valeur de 20 % ne suffit pas, consultez la documentation relative à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur la façon de la modifier.  

### <a name="avoid-clearing-workspaces-when-executing-r-code-in-a-includessnoversiontokenssnoversionmdmd-compute-context"></a>Éviter l’effacement d’espaces de travail lors de l’exécution de code R dans un contexte de calcul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 Si vous utilisez la commande R pour effacer des objets de votre espace de travail lors de l’exécution du code R dans un contexte de calcul [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou si vous effacez l’espace de travail dans le cadre d’un script R appelé avec [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), vous pouvez obtenir l’erreur : *objet d’espace de travail revoScriptConnection introuvable*

`revoScriptConnection` est un objet dans l’espace de travail R qui contient des informations sur une session R appelée à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Toutefois, si votre code R inclut une commande pour effacer l’espace de travail (comme `rm(list=ls()))`) toutes les informations sur la session et les autres objets dans l’espace de travail R sont également effacés.

Pour résoudre ce problème, évitez l’effacement global de variables et d’autres objets lors de l’exécution de R [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Bien que l’effacement de l’espace de travail soit courant lorsque vous travaillez dans la console R, il peut avoir des conséquences inopinées. 

+ Pour supprimer des variables spécifiques, utilisez la fonction de *suppression* de R : `remove('name1', 'name2', ...)` 
+ Si plusieurs variables sont à supprimer, enregistrez les noms des variables temporaires dans une liste et effectuez un nettoyage périodique. 
   
### <a name="restrictions-on-data-that-can-be-provided-as-input-to-an-r-script"></a>Restrictions sur les données qui peuvent être fournies comme entrée à un script R  
 Dans un script R, vous ne pouvez pas utiliser les types de résultats de requête suivants :  
  
-   Données issues d’une requête [!INCLUDE[tsql](../../includes/tsql-md.md)] qui référence des colonnes à chiffrement intégral.  
  
-   Données issues d’une requête [!INCLUDE[tsql](../../includes/tsql-md.md)] qui référence des colonnes masquées.  
  
     Si vous avez besoin d’utiliser des données masquées dans un script R, une solution de contournement possible consiste à effectuer une copie des données dans une table temporaire et à utiliser ces données à la place.  
   
  
## <a name="microsoft-r-server-standalone"></a>Microsoft R Server (autonome)  
 Cette section répertorie les problèmes spécifiques à la version autonome de Microsoft R Server. 
  
### <a name="multiple-r-libraries-and-executables-are-installed-if-you-install-both-standalone-and-in-database"></a>Plusieurs bibliothèques et fichiers exécutables R sont installés en cas d’installation autonome et dans la base de données  
 Le programme de configuration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] offre désormais la possibilité d’installer Microsoft R Server (autonome). L’option Microsoft R Server (autonome) peut être utilisée dans Enterprise Edition pour installer un serveur Windows autonome prenant en charge R, mais ne nécessitant pas d’interactivité avec SQL Server.    

> [!TIP] Cette option autonome n’est **pas** requise pour utiliser R avec [!INCLUDE[tsql](../../includes/tsql-md.md)].
> 
> Si vous avez besoin de configurer un ordinateur client de science des données capable de se connecter à [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] ou à Microsoft R Server (autonome), nous vous recommandons [Microsoft R Client](http://go.microsoft.com/fwlink/?LinkId=799768).  

Si vous installez R Services (dans la base de données) et Microsoft R Server (autonome) sur le même ordinateur, n’oubliez pas qu’une instance R distincte sera créée pour chaque instance de SQL Server pour laquelle R est activé, ainsi que pour Microsoft R Server (autonome).  Par exemple, si vous avez installé l’instance par défaut et une instance nommée, ainsi que R Server (autonome), vous pouvez avoir trois instances R sur le même ordinateur :  
  
-   **Autonome :** C:\Program Files\Microsoft SQL Server\130\R_SERVER  
  
-   **Instance par défaut :** C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES  
  
-   **Instance nommée :** C:\Program Files\Microsoft SQL Server\MSSQL13.<nom_instance>\R_SERVICES  
  
> [!NOTE] 
> 
> Utiliser les bibliothèques et les outils R associés à une instance de base de données uniquement dans le contexte de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Si vous avez besoin d’exécuter R à l’aide d’autres outils R, veillez à référencer les bibliothèques R utilisées par R Server (autonome), installées par défaut dans C:\Program Files\Microsoft SQL Server\130\R_SERVER.  

### <a name="performance-limits-when-r-services-libraries-are-called-from-standalone-r-tools"></a>Limites de performance lors de l’appel de bibliothèques R Services à partir d’outils autonomes R

Les bibliothèques R utilisées par SQL Server R Services sont installées par défaut dans C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES. Il est *possible* d’appeler les outils et bibliothèques R installés pour SQL Server R Services à partir d’une application R externe telle que RGui. 

Cependant, si vous procédez ainsi, les performances seront limitées. Par exemple, même si vous avez acheté SQL Server Enterprise Edition, R s’exécutera en monothread si vous exécutez votre code R à l’aide d’outils externes. Les performances seront supérieures si vous exécutez votre code R si vous établissez une connexion SQL Server et utilisez [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md), qui appelle les bibliothèques R Services pour vous.

+ Évitez d’appeler les bibliothèques R utilisées par SQL Server à partir d’outils R externes. 
+ Si vous avez besoin d’exécuter R sur l’ordinateur SQL Server à l’aide d’outils externes, vous devez installer une instance distincte de R, puis vérifier que vos outils R pointent vers la nouvelle bibliothèque. 
+ Si vous utilisez Enterprise Edition, nous vous recommandons d’installer Microsoft R Server (autonome) sur l’ordinateur SQL Server. Ensuite, à partir de l’outil externe que vous utilisez pour exécuter le code R, référencez des bibliothèques pour R Server, qui sont installées par défaut dans C:\Program Files\Microsoft SQL Server\<numéro de version>\R_SERVER. 

Pour plus d’informations, consultez [Créer un R Server autonome](../../advanced-analytics/r-services/create-a-standalone-r-server.md).  
  
  
## <a name="general-r-issues"></a>Problèmes généraux liés à R  

 Cette section répertorie les problèmes propres à la connectivité et aux outils de performance de R.  
  
### <a name="limited-support-for-sql-data-types-in-spexecuteexternalscript"></a>Prise en charge limitée des types de données SQL dans sp_execute_external_script  

 Tous les types de données pris en charge dans SQL ne peuvent pas être utilisés dans R. Pour résoudre ce problème, envisagez de convertir le type de données non pris en charge pour un type de données pris en charge avant de transmettre les données à sp_execute_external_script.  
  
 Pour plus d’informations, consultez [Utilisation des types de données R](../../advanced-analytics/r-services/working-with-r-data-types.md).  
  
### <a name="possible-string-corruption"></a>Corruption de chaîne possible  

 Tout aller-retour de données de type chaîne depuis [!INCLUDE[tsql](../../includes/tsql-md.md)] vers R, puis à nouveau vers [!INCLUDE[tsql](../../includes/tsql-md.md)] , peut provoquer une corruption. Cela est dû aux différents codages utilisés dans R et dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ainsi qu’aux différents classements et langues pris en charge dans R et [!INCLUDE[tsql](../../includes/tsql-md.md)]. Toute chaîne dans un codage non-ASCII risque d’être gérée de façon incorrecte.  
  
 Quand vous envoyez des données de type chaîne vers R, convertissez-les en une représentation ASCII, si possible.  
  
### <a name="only-one-raw-value-can-be-returned-from-spexecuteexternalscript"></a>Une seule valeur brute peut être retournée par sp_execute_external_script  

 Quand un type de données binaire (type de données **raw** R) est retourné à partir de R, la valeur doit être la valeur de la trame de données de sortie.  
  
 La prise en charge de plusieurs sorties **raw** sera ajoutée dans les versions ultérieures.  
  
 Si vous souhaitez plusieurs jeux de sortie, vous pouvez effectuer plusieurs appels de la procédure stockée et envoyer les jeux de résultats à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’aide d’ODBC.  
  
 Notez que vous pouvez renvoyer des valeurs de paramètres avec les résultats de la procédure stockée en ajoutant simplement le mot clé OUTPUT. Pour plus d’informations, consultez [Retour de données à l’aide de paramètres OUTPUT](https://technet.microsoft.com/library/ms187004.aspx).
  
### <a name="loss-of-precision"></a>Perte de précision  

 [!INCLUDE[tsql](../../includes/tsql-md.md)] et R prennent en charge différents types de données ; ainsi, les types de données numériques peuvent subir une perte de précision pendant la conversion.  
  
 Pour plus d'informations sur la conversion implicite de types de données, consultez [Working with R Data Types](../../advanced-analytics/r-services/working-with-r-data-types.md).  
  
### <a name="variable-scoping-error-the-sample-data-set-for-the-analysis-has-no-variables-when-using-the-transformfunc-parameter"></a>Erreur de portée de variable « The sample data set for the analysis has no variables » (« L’exemple de jeu de données pour l’analyse n’a aucune variable ») quand le paramètre transformFunc est utilisé  

 Vous pouvez passer un argument *transfoumFunc* dans une fonction telle que `rxLinmod` ou `rxLogit` to transfoum the data while modelling. Toutefois, les appels de fonction imbriqués peuvent entraîner des erreurs de portée dans le contexte de calcul de SQL Server, même si les appels fonctionnent correctement dans le contexte de calcul local.  
  
 Par exemple, supposons que vous avez défini deux fonctions `f` et `g` dans votre environnement global local, et que `g` appelle `f`. Dans les appels distribués ou distants impliquant `g`, l’appel à `g` risque d’échouer car `f` est introuvable, même si vous avez transmis à la fois `f` et `g` à l’appel distant.  
  
 Si vous rencontrez ce problème, vous pouvez le résoudre en incorporant la définition de `f` dans votre définition de `g`, n’importe où avant l’appel habituel de `g` par `f`.  
  
 Exemple :  
  
```  
f <- function(x) { 2*x + 3 }  
g <- function(y) {   
              a <- 10 * y  
               f(a)  
}  
  
```  
  
 Pour éviter cette erreur, réécrivez le code comme suit :  
  
```  
g <- function(y){  
              f <- function(x) { 2*x +3}  
              a <- 10 * y  
              f(a)  
}  
  
```  

  
## <a name="revolution-r-enterprise-and-microsoft-r-open"></a>Revolution R Enterprise et Microsoft R Open 
 
 Cette section répertorie les problèmes propres aux outils de connectivité, de développement et de performances de R fournis par Revolution Analytics. Ces outils ont été fournis dans les versions préliminaires de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 

En général, nous recommandons la désinstallation de ces versions précédentes et l’installation de la dernière version de SQL Server R Services, Microsoft R Server ou Microsoft R Client.
  
### <a name="running-side-by-side-versions-of-revolution-r-enterprise"></a>Exécution de versions côte à côte de Revolution R Enterprise  

 L’installation de Revolution R Enterprise côte à côte avec toute version de [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)] n’est pas prise en charge.  
  
 Si vous avez une licence pour utiliser une version différente de Revolution R Enterprise, vous devez la placer sur un ordinateur autre que celui de l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et que toute station de travail que vous souhaitez utiliser pour vous connecter à l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="limited-support-for-revoscaler-rxexec"></a>Prise en charge limitée de RevoScaleR rxExec  

 À compter de RC0, la fonction `rxExec` fournie par [!INCLUDE[rsql_rre-short](../../includes/rsql-rre-short-md.md)] ne peut être utilisée qu’en mode monothread.  
  
 Le parallélisme de `rxExec` entre plusieurs processus sera ajouté dans une prochaine version.  
  
### <a name="data-import-and-manipulation-using-revoscaler"></a>Importation et manipulation de données à l’aide de RevoScaleR  

 Pendant la lecture de colonnes **varchar** à partir d’une base de données, les espaces sont supprimés. Pour éviter cela, placez les chaînes entre caractères autres qu’un espace.  
  
 Quand vous utilisez des fonctions telles que `rxDataStep` pour créer des tables de base de données comportant des colonnes **varchar** , la largeur des colonnes est estimée en fonction d’un échantillon des données. Si la largeur peut varier, il est peut-être nécessaire de remplir toutes les chaînes afin qu’elles aient une longueur commune.  
  
 L’utilisation d’une transformation pour modifier le type de données d’une variable n’est pas prise en charge quand des appels répétés à `rxImport` ou `rxTextToXdf` sont effectués pour importer et ajouter des lignes, combinant plusieurs fichiers d’entrée dans un fichier .xdf unique.  
  
### <a name="increase-maximum-parameter-size-to-support-rxgetvarinfo"></a>Augmenter la taille de paramètre maximale pour prendre en charge rxGetVarInfo  

 Si vous utilisez des jeux de données avec un très grand nombre de variables (par exemple, plus de 40 000), vous devez définir l’indicateur `max-ppsize` au démarrage de R pour utiliser des fonctions telles que `rxGetVarInfo`.  L’indicateur `max-ppsize` spécifie la taille maximale de la pile de protection du pointeur.  
  
 Si vous utilisez la console R (par exemple, dans rgui.exe ou rterm.exe), vous pouvez définir la valeur de max-ppsize sur 500000 en tapant :  
  
```  
R --max-ppsize=500000  
```  
  
 Si vous utilisez l’environnement [!INCLUDE[rsql_developr](../../includes/rsql-developr-md.md)] , vous pouvez définir l’indicateur `max-ppsize` en appelant l’exécutable RevoIDE comme suit :  
  
```  
RevoIDE.exe /RCommandLine --max-ppsize=500000  
```  
  
### <a name="issues-with-rxdtree-function"></a>Problèmes liés à la fonction rxDTree  

 La fonction `rxDTree` ne prend pas en charge actuellement les transformations dans les formules. En particulier, l’utilisation de la syntaxe `F()` pour créer des facteurs à la volée n’est pas prise en charge. Toutefois, les données numériques sont automatiquement placées dans un conteneur.  
  
 Les facteurs ordonnés sont traités de la même façon que les facteurs dans toutes les fonctions d’analyse RevoScaleR, sauf `rxDTree`.  
  
### <a name="using-the-r-productivity-environment"></a>Utilisation de R Productivity Environment  

Certaines versions préliminaires de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] incluaient un environnement de développement R pour Windows qui a été créé par Revolution Analytics. 

Toutefois, pour la compatibilité avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], nous recommandons vivement d’installer Microsoft R Client ou Microsoft R Server plutôt que les outils Revolution Analytics. Les [outils R pour Visual Studio](https://www.visualstudio.com/vs/rtvs/) sont un autre client recommandé qui prend en charge les solutions Microsoft R.
  
### <a name="compatibility-issues-with-sqlite-odbc-driver-and-revoscaler"></a>Problèmes de compatibilité avec le pilote ODBC de SQLite et RevoScaleR  
 La révision 0.92 du pilote ODBC de SQLite est incompatible avec RevoScaleR tandis que les révisions 0.88 à 0.91, 0.93 et ultérieur sont connues pour être compatibles.  
  
## <a name="see-also"></a>Voir aussi  
[Nouveautés de SQL Server 2016](../../sql-server/what-s-new-in-sql-server-2016.md)
  