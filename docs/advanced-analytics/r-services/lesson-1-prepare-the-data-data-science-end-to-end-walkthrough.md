---
title: "Le&#231;on 1 : Pr&#233;parer les donn&#233;es (Proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/18/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: 65fd41d4-c94e-4929-a24a-20e792a86579
caps.latest.revision: 29
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 25
---
# Le&#231;on 1 : Pr&#233;parer les donn&#233;es (Proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es)
Pour préparer cette procédure pas à pas, vous devrez effectuer les opérations suivantes :

1. Télécharger les données et tous les scripts R utilisés dans la procédure pas à pas. Un script PowerShell est fourni pour simplifier le téléchargement à partir de GitHub.   

2. Installer des packages R supplémentaires, à la fois sur le serveur et sur votre station de travail R.  

3. Préparer l’environnement, y compris la base de données et les données utilisées pour la modélisation et le calcul de score.
 
    Pour ce faire, vous utiliserez un deuxième script PowerShell, RunSQL_R_Walkthrough.ps1.
    Ce script configure la base de données et charge les données dans la table que vous spécifiez.  Il crée également des fonctions SQL et des procédures stockées qui simplifient les tâches de science des données. 
 

## <a name="1-download-the-data-and-scripts"></a>1. Télécharger les données et les scripts  
Tout le code dont vous aurez besoin pour effectuer cette procédure pas à pas est fourni dans un dépôt GitHub. Vous pouvez utiliser un script PowerShell pour créer une copie locale des fichiers.  
  
#### <a name="to-download-all-scripts-using-powershell"></a>Pour télécharger tous les scripts à l’aide de PowerShell  
  
1.  Sur votre ordinateur client de science des données, ouvrez une invite de commandes Windows PowerShell en tant qu’administrateur.  
  
2.  Si vous n’avez encore jamais exécuté PowerShell sur cette instance, ou si vous n’êtes pas autorisé à exécuter des scripts, une erreur peut survenir. Dans ce cas, exécutez cette commande avant d’exécuter le script, pour autoriser temporairement les scripts sans modifier les paramètres par défaut du système.  
  
    ```  
    Set-ExecutionPolicy Unrestricted -Scope Process -Force  
    ```  
  
3.  Exécutez la commande suivante pour télécharger les fichiers de script dans un répertoire local. Si vous ne spécifiez pas un autre répertoire, par défaut le dossier C:\tempR est créé et tous les fichiers y sont enregistrés.  
  
    ```  
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_R_Walkthrough.ps1'  
    $ps1_dest = "$pwd\Download_Scripts_R_Walkthrough.ps1"  
    $wc = New-Object System.Net.WebClient  
    $wc.DownloadFile($source, $ps1_dest)  
    .\Download_Scripts_R_Walkthrough.ps1 –DestDir 'C:\tempR'  
  
    ```  
  
    Si vous souhaitez enregistrer les fichiers dans un répertoire différent, modifiez les valeurs du paramètre *DestDir* et spécifiez un dossier différent sur votre ordinateur. Si vous saisissez un nom de dossier qui n’existe pas, le script PowerShell créera le dossier pour vous.  
  
4.  Une fois le téléchargement terminé, la console de commande Windows PowerShell doit ressembler à ceci :  
  
    ![After completion of PowerShell script](../../advanced-analytics/r-services/media/rsql-e2e-psscriptresults.PNG "After completion of PowerShell script")  
  
5.  Dans la console PowerShell, vous pouvez exécuter la commande `ls` pour afficher la liste des fichiers qui ont été téléchargés dans *DestDir*.  Pour une liste et une description des fichiers, consultez la section [Contenu du téléchargement](#What-the-Download-Includes).
  
## <a name="2-install-required-packages"></a>2. Installer les packages nécessaires  
Cette procédure pas à pas nécessite certaines bibliothèques R qui ne sont pas installées par défaut dans le cadre de [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Vous devez installer les packages à la fois sur le client où vous développerez la solution et sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où vous déploierez la solution.  
  
### <a name="install-required-packages-on-the-client"></a>Installer les packages nécessaires sur le client  
Le script R que vous avez téléchargé contient les commandes pour télécharger et installer ces packages.  
  
1.  Dans votre environnement R, ouvrez le fichier de script RSQL_R_Walkthrough.R.  
  
2.  Mettez en surbrillance et exécutez ces lignes.  
  
    ```  
    # Install required R libraries for this walkthrough if they are not installed.   
  
    if (!('ggmap' %in% rownames(installed.packages()))){  
      install.packages('ggmap')  
    }  
    if (!('mapproj' %in% rownames(installed.packages()))){  
      install.packages('mapproj')  
    }  
    if (!('ROCR' %in% rownames(installed.packages()))){  
      install.packages('ROCR')  
    }  
    if (!('RODBC' %in% rownames(installed.packages()))){  
      install.packages('RODBC')  
    }  
    ```  
  
### <a name="install-required-packages-on-the-server"></a>Installer les packages nécessaires sur le serveur  

  
1.  Sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ouvrez RGui.exe en tant qu’administrateur.  Si vous avez installé SQL Server R Services à l’aide des paramètres par défaut, vous trouverez RGui.exe dans C:\Program Files\Microsoft SQL Server\MSSQL13. MSSQLSERVER\R_SERVICES\bin\x64).  
  
    Ou, si vous avez installé un autre environnement R sur l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (par exemple, RStudio), vous pouvez utiliser la console R pour exécuter les commandes.  
  
2.  À l’invite R, exécutez les commandes R suivantes :  
  
    ```  
    install.packages("ggmap", lib=grep("Program Files", .libPaths(), value=TRUE)[1])  
    install.packages("mapproj", lib=grep("Program Files", .libPaths(), value=TRUE)[1]) 
    install.packages("ROCR", lib=grep("Program Files", .libPaths(), value=TRUE)[1]) 
    install.packages("RODBC", lib=grep("Program Files", .libPaths(), value=TRUE)[1]) 
    ```  
  
**Remarques :**  
  
-   Cet exemple utilise la fonction grep R pour rechercher le vecteur de chemins disponibles et trouver celui qui se trouve dans « Program Files ». Pour plus d’informations, consultez [http://www.rdocumentation.org/packages/base/functions/grep](http://www.rdocumentation.org/packages/base/functions/grep).   
  
-   Si vous pensez que les packages sont déjà installés, vérifiez la liste des packages installés à l’aide de la fonction R, `installed.packages()`.  
  
-   Vous pouvez installer une bibliothèque utilisateur sur le client si vous ne pouvez pas écrire dans la bibliothèque principale dans Program Files. Toutefois, lorsque vous installez les packages sur l’ordinateur SQL Server, vous devez les installer dans la bibliothèque par défaut utilisée par SQL Server R Services. N’utilisez pas une bibliothèque utilisateur. Pour plus d’informations, consultez [Installer des packages R supplémentaires sur SQL Server](../../advanced-analytics/r-services/install-additional-r-packages-on-sql-server.md).
      

## <a name="3-run-powershell-script-runsqlrwalkthroughps1"></a>3. Exécuter le script PowerShell RunSQL_R_Walkthrough.ps1  

Vous pouvez exécuter ce script PowerShell sur l’ordinateur sur lequel vous allez créer la solution, par exemple l’ordinateur pour le développement et le test de votre code R. Cet ordinateur doit pouvoir se connecter à l’ordinateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide du protocole Canaux nommés.  
  
Le script effectue les actions suivantes :  
  
-   Il vérifie si SQL Native Client et les utilitaires de ligne de commande pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont installés. Les outils en ligne de commande sont nécessaires pour exécuter [l’utilitaire bcp](../../tools/bcp-utility.md), qui est utilisé pour le chargement en bloc rapide des données dans les tables SQL.    
-   Il se connecte à l’instance spécifiée de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et exécute certains scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] qui configurent la base de données et créent les tables pour le modèle et les données.    
-   Il exécute un script SQL pour créer plusieurs procédures stockées.    
-   Il charge les données que vous avez téléchargées précédemment dans la table nyctaxi_sample.    
-   Il réécrit les arguments dans le fichier de script R pour utiliser le nom de base de données que vous spécifiez. 

### <a name="to-run-the-script"></a>Pour exécuter le script
  
1.  Ouvrez une ligne de commande PowerShell en tant qu’administrateur.    
  
2.  Accédez au dossier où vous avez téléchargé les scripts et tapez le nom du script comme indiqué. Appuyez sur Entrée.  
  
    ```  
    .\RunSQL_R_Walkthrough.ps1  
    ```  
  
3.  Une invite s’affiche pour chacun des paramètres suivants :  
  
    - Le nom de la base de données que vous voulez créer. 
      Par exemple, vous pouvez saisir **Didacticiel** ou **Taxi**.  
    - Les informations d’identification sous lesquelles exécuter le script. Deux options s’offrent à vous :
        + Saisissez le nom d’une session SQL qui possède des privilèges CREATE DATABASE et fournissez le mot de passe SQL sur une invite suivante.
        + Appuyez sur ENTRÉE sans saisir de nom pour utiliser votre propre identité Windows, puis, à l’invite sécurisée, saisissez votre mot de passe Windows... PowerShell n’autorise pas la saisie d’un nom d’utilisateur Windows différent. 

          Si vous ne parvenez pas à spécifier un utilisateur valide, le script ne pourra pas utiliser l’authentification Windows intégrée.  
  
    -   Le chemin d’accès complet du fichier csv que vous souhaitez charger dans la base de données.  
  
        Le script doit télécharger le fichier et charger les données dans la base de données automatiquement, mais en cas d’échec, vous pouvez toujours charger les données manuellement.  
  
4.  Appuyez sur Entrée pour exécuter le script.  
  
## <a name="troubleshooting"></a>Dépannage  
 
 Si vous rencontrez des problèmes, vous pouvez exécuter tout ou partie des étapes manuellement, à l’aide des lignes du script PowerShell comme exemples. 
 

### <a name="the-powershell-script-didnt-download-the-data"></a>Le script PowerShell n’a pas téléchargé les données
  
Pour télécharger les données manuellement, cliquez avec le bouton droit sur le lien suivant et sélectionnez **Enregistrer la cible sous**.  
  
[http://getgoing.blob.core.windows.net/public/nyctaxi1pct.csv](http://getgoing.blob.core.windows.net/public/nyctaxi1pct.csv)  
  
Prenez note du chemin du fichier de données téléchargé et du nom du fichier où les données ont été enregistrées. Vous aurez besoin de ce chemin pour charger les données dans la table à l’aide de **bcp**.  
  
### <a name="i-was-unable-to-download-the-data"></a>Je n’ai pas pu télécharger les données
Le fichier de données est volumineux. Utilisez un ordinateur qui dispose d’une connexion Internet relativement bonne, sinon le téléchargement risque d’expirer.  

  
### <a name="could-not-connect-or-script-failed"></a>Connexion impossible ou échec du script  
  
+ Vérifiez l’orthographe du nom de l’instance. 
+ Vérifiez la chaîne de connexion complète.    
+ En fonction des spécifications de votre réseau, le nom d’instance peut nécessiter une qualification avec un ou plusieurs noms de sous-réseaux.  Par exemple, si MYSERVER ne fonctionne pas, essayez myserver.subnet.mycompany.com.
  
### <a name="network-error-or-protocol-not-found"></a>Erreur réseau ou protocole introuvable  
  
+ Vérifiez que l’instance prend en charge les connexions à distance.    
+ Vérifiez que l’utilisateur SQL spécifié peut se connecter à distance à la base de données, et que Canaux nommés est activé sur l’instance.    
+ Vérifiez les autorisations du compte. Le compte que vous avez spécifié n’est peut-être pas autorisé à créer une base de données et à charger des données.  

### <a name="bcp-did-not-run"></a>bcp ne s’est pas exécuté  

+ Vérifiez que [l’utilitaire bcp](../../tools/bcp-utility.md) est disponible sur votre ordinateur. Vous pouvez exécuter bcp à partir d’une fenêtre PowerShell ou d’une invite de commandes Windows.
+ Si une erreur se produit, ajoutez l’emplacement de l’utilitaire bcp à la variable d’environnement système PATH et réessayez.  

### <a name="the-table-schema-was-created-but-there-is-no-data-in-the-table"></a>Le schéma de table a été créé, mais aucune donnée ne se trouve dans la table

Si le reste du script s’est exécuté sans problème, vous pouvez charger les données dans la table manuellement en appelant **bcp** à partir de la ligne de commande, comme suit :  


 
**Avec une session SQL**
    
~~~~ 
bcp TutorialDB.dbo.nyctaxi_sample in c:\tempR\nyctaxi1pct.csv -t ',' -S rtestserver.contoso.com -f C:\tempR\taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -U <SQL login> -P <password  
~~~~  
  
**Avec l’authentification Windows**  

~~~~
bcp TutorialDB.dbo.nyctaxi_sample in c:\tempR\nyctaxi1pct.csv -t ',' -S rtestserver.contoso.com -f C:\tempR\taxiimportfmt.xml -F 2 -C "RAW" -b 200000 -T 
~~~~ 
  
  
+ Le mot-clé **in** indique la direction du déplacement des données.  
+ L’argument **-f** requiert que vous spécifiiez le chemin d’accès complet d’un fichier de format. Un fichier de format est nécessaire si vous utilisez l’option **in**.
+ Utilisez les arguments **-U** et **-P** si vous exécutez bcp avec une session SQL.
+ Utilisez l’argument **-T** si vous utilisez l’authentification intégrée Windows. 

  
### <a name="how-can-i-run-the-script-without-prompts"></a>Comment puis-je exécuter le script sans invite ?  
  
Vous pouvez spécifier tous les paramètres sur une seule ligne de commande, en utilisant des valeurs propres à votre environnement. 
  
```  
.\RunSQL_R_Walkthrough.ps1 -server <server address> -dbname <new db name> -u <user name> -p <password> -csvfilepath <path to csv file>  
```  
  
Par exemple, pour exécuter le script avec une session SQL :  
  
```  
.\RunSQL_R_Walkthrough.ps1 -server MyServer.subnet.domain.com -dbname MyDB –u SqlUserName –p SqlUsersPassword -csvfilepath C:\temp\nyctaxi1pct.csv  
```  
  
L'exemple réalise les actions suivantes :  
  
-   Il se connecte à l’instance et à la base de données spécifiées avec les informations d’identification de *SqlUserName*.  
-   Il obtient les données à partir du fichier *C:\temp\nyctaxi1pct.csv*.  
-   Il charge les données dans la table *dbo.nyctaxi_sample*, dans la base de données *MyDB* sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nommée *MyServer*.  

### <a name="the-data-loaded-but-it-contains-duplicates"></a>Les données sont chargées, mais il y a des doublons

S’il existe déjà une table avec le schéma correct, bcp continue à s’exécuter, mais va insérer une nouvelle copie des données plutôt que de remplacer les données existantes. Des données seront alors dupliquées.  Veillez à tronquer les tables existantes avant de réexécuter le script.

## <a name="what-the-download-includes"></a>Contenu du téléchargement

Lorsque vous téléchargez les fichiers à partir du référentiel GitHub, vous obtenez les éléments suivants :
+ Des données au format CSV
+ Un script PowerShell pour la préparation de l’environnement
+ Un fichier de format XML pour l’importation des données vers SQL Server à l’aide de bcp
+ Plusieurs scripts T-SQL
+ Tout le code R dont vous avez besoin pour cette procédure pas à pas

### <a name="training-and-scoring-data"></a>Données de formation et de calcul de score  
Les données sont un échantillon représentatif du jeu de données sur les taxis de la ville de New York, qui contient les enregistrements de plus de 173 millions de trajets en 2013, y compris les tarifs et le montant des pourboires versés pour chaque trajet.  Pour plus d’informations sur la collecte initiale de ces données et sur la façon d’obtenir le jeu de données complet, consultez  
[http://chriswhong.com/open-data/foil_nyc_taxi/](http://chriswhong.com/open-data/foil_nyc_taxi/).  
  
Pour rendre les données plus faciles à manipuler, l’équipe de science des données Microsoft a effectué un sous-échantillonnage pour obtenir seulement 1 % des données.  Ces données a été partagées dans un conteneur de stockage d’objets blob public dans Azure, au format .CSV. La source de données est un fichier non compressé, d’un peu moins de 350 Mo.  
 
### <a name="files"></a>Fichiers

 
+ **RunSQL_R_Walkthrough.ps1** Vous exécuterez ce script en premier, à l’aide de PowerShell. Il appelle les scripts SQL pour charger les données dans la base de données.  
    
+ **taxiimportfmt.xml** Un fichier de définition de format utilisé par l’utilitaire bcp pour charger des données dans la base de données.
      
+ **RSQL_R_Walkthrough.R** Il s’agit du script R de base qui sera utilisé dans le reste des leçons pour l’analyse des données et la modélisation. Il fournit tout le code R dont vous avez besoin pour explorer les données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , générer le modèle de classification et de créer des tracés.   
  
### <a name="sql-scripts"></a>Scripts SQL  
Ce script PowerShell exécute plusieurs scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] sur le serveur. Le tableau suivant répertorie les fichiers de script [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
|Nom du fichier de script SQL|Ce qu’il fait|  
|------------------------|----------------|  
|create-db-tb-upload-data.sql|Crée une base de données et deux tables :<br /><br /> *nyctaxi_sample* : table qui contient les données de formation, un échantillon de 1 % du jeu de données sur les taxis de New York. Un index cluster columnstore est ajouté à la table pour améliorer les performances de stockage et des requêtes.<br /><br /> *nyc_taxi_models* : table vide que vous utiliserez ultérieurement pour enregistrer le modèle de classification formé.|  
|PredictTipBatchMode.sql|Crée une procédure stockée qui appelle un modèle formé pour prédire les étiquettes des nouvelles observations. Il accepte une requête comme paramètre d’entrée.|  
|PredictTipSingleMode.sql|Crée une procédure stockée qui appelle un modèle de classification formé pour prédire les étiquettes des nouvelles observations. Les variables des nouvelles observations sont passées comme paramètres inline.|  
|PersistModel.sql|Crée une procédure stockée qui permet de stocker la représentation binaire du modèle de classification dans une table de la base de données.|  
|fnCalculateDistance.sql|Crée une fonction scalaire SQL qui calcule la distance directe entre les lieux de prise en charge et de dépose.|  
|fnEngineerFeatures.sql|Crée une fonction table SQL qui crée les caractéristiques d’apprentissage du modèle de classification.|  
  
Toutes les requêtes SQL utilisées dans cette procédure ont été testées et peuvent être exécutées telles quelles dans votre code R. Toutefois, si vous souhaitez faire des expérimentations supplémentaires ou développer votre propre solution à l’aide de requêtes SQL, nous vous recommandons d’utiliser un environnement de développement tel que [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour tester et optimiser vos requêtes avant de les ajouter à votre code R.  
  
  
## <a name="next-lesson"></a>Leçon suivante  
[Leçon 2 : Afficher et explorer les données &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-2-view-and-explore-the-data-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Leçon précédente  
[Procédure pas à pas pour une solution complète de science des données](../../advanced-analytics/r-services/data-science-end-to-end-walkthrough.md)  
  
  
  
