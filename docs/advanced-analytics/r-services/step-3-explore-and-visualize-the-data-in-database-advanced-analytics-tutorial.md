---
title: "&#201;tape 3 : Explorer et visualiser les donn&#233;es (didacticiel sur l’analytique avanc&#233;e en base de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
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
  - "TSQL"
ms.assetid: 7fe670f3-5e62-43ef-97eb-b9af54df9128
caps.latest.revision: 11
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 11
---
# &#201;tape 3 : Explorer et visualiser les donn&#233;es (didacticiel sur l’analytique avanc&#233;e en base de donn&#233;es)
Le développement d’une solution de science des données comprend généralement l’exploration et la visualisation des données. Lors de cette étape, vous allez examiner les exemples de données, puis générer des tracés à l’aide de fonctions R. Ces fonctions R sont déjà incluses dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]. Dans cette procédure pas à pas, vous allez vous entraîner à appeler des fonctions R à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## Examiner les données  
Tout d’abord, prenez une minute pour examiner les exemples de données, si ce n’est déjà fait.  
  
Dans le dataset d’origine, les identificateurs de taxis et les enregistrements de trajets ont été fournis dans des fichiers distincts. Toutefois, pour simplifier l’utilisation des exemples de données, les deux datasets d’origine ont été joints sur les colonnes _medallion_, _hack_license_ et _pickup_datetime_.  Les enregistrements ont aussi été échantillonnés pour obtenir seulement 1 % du nombre d’enregistrements d’origine. Le dataset échantillonné obtenu compte 1 703 957 lignes et 23 colonnes.  
  
**Identificateurs de taxis**  
  
-   La colonne _medallion_ représente le numéro d’ID unique du taxi.  
  
-   La colonne _hack_license_ contient le numéro de licence du conducteur du taxi (anonyme).  
  
**Enregistrements de trajets et de prix**  
  
-   Chaque enregistrement de trajet comprend les lieux de prise en charge et de dépose, ainsi que la durée et la distance du trajet.  
  
-   Chaque enregistrement de prix inclut des informations telles que le type de paiement, le montant total du paiement et le montant du pourboire.  
  
-   Les trois dernières colonnes peuvent être utilisées pour différentes tâches d’apprentissage automatique.  La colonne _tip_amount_ contient des valeurs numériques continues et peut être utilisée comme colonne **étiquette** pour l’analyse de régression. La colonne _tipped_ contient seulement des valeurs oui/non. Elle sert à la classification binaire. La colonne _tip_class_ a plusieurs **étiquettes de classes**, et peut donc être utilisée comme étiquette pour les tâches de classification multiclasse.  
  
    Cette procédure pas à pas ne montre que la tâche de classification binaire. Si vous le souhaitez, vous pouvez essayer de créer des modèles pour les autres deux tâches d’apprentissage automatique, la régression et la classification multiclasse.  
  
-   Les valeurs utilisées pour les colonnes d’étiquettes sont basées sur la colonne _tip_amount_, à l’aide de ces règles d’entreprise :  
  
    |Nom de la colonne dérivée|Règle|  
    |-|-|  
     |tipped|Si tip_amount > 0, tipped = 1, sinon tipped = 0|  
    |tip_class|Classe 0 : tip_amount = 0 $<br /><br />Classe 1 : tip_amount > 0 $ et tip_amount <= 5 $<br /><br />Classe 2 : tip_amount > 5 $ et tip_amount <= 10 $<br /><br />Classe 3 : tip_amount > 10 $ et tip_amount <= 20 $<br /><br />Classe 4 : tip_amount > 20 $|  
  
## Créer des tracés à l’aide de R en T-SQL  
La visualisation étant un outil tellement puissant pour comprendre la distribution des données et des valeurs hors norme, R fournit de nombreux packages de visualisation de données. La distribution open source standard de R inclut également de nombreuses fonctions pour créer des histogrammes, des nuages de points, des diagrammes à surface et d’autres graphiques d’exploration de données.  
  
R crée généralement des images à l’aide d’un périphérique R pour la sortie graphique. Vous pouvez capturer la sortie de ce périphérique et stocker l’image dans un type de données **varbinary** pour le rendu dans une application, ou vous pouvez enregistrer les images dans l’un des formats de fichiers pris en charge (.JPG, .PDF, etc.).  
  
Dans cette section, vous allez apprendre à travailler avec chaque type de sortie à l’aide de procédures stockées.  
  
-   Stockage de tracés en tant que type de données varbinary  
  
-   Enregistrement de tracés dans des fichiers (.JPG, .PDF) sur le serveur  
  
### Stockage de tracés en tant que type de données varbinary  
Vous allez utiliser `rxHistogram`, l’une des fonctions R améliorées fournies avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)], pour tracer un histogramme basé sur les données obtenues à partir d’une requête [!INCLUDE[tsql](../../includes/tsql-md.md)]. Pour faciliter l’appel de la fonction R, vous allez l’encapsuler dans une procédure stockée, _PlotHistogram_.  
  
La procédure stockée retourne l’image sous forme de flux de données varbinary qui, évidemment, ne peut pas être affiché directement. Toutefois, vous pouvez utiliser l’utilitaire **bcp** pour obtenir les données varbinary et les enregistrer en tant que fichier image sur un ordinateur client.  
  
##### Pour créer la procédure stockée PlotHistogram  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez une nouvelle fenêtre de requête.  
  
2.  Sélectionnez la base de données pour la procédure pas à pas, puis créez la procédure à l’aide de cette instruction.  
  
    ```  
    CREATE PROCEDURE [dbo].[PlotHistogram]  
    AS  
    BEGIN  
      SET NOCOUNT ON;  
      DECLARE @query nvarchar(max) =  
      N'SELECT tipped FROM nyctaxi_sample'  
      EXECUTE sp_execute_external_script @language = N'R',  
                                         @script = N'  
       image_file = tempfile();  
       jpeg(filename = image_file);  
       #Plot histogram  
       rxHistogram(~tipped, data=InputDataSet, col=''lightgreen'',   
       title = ''Tip Histogram'', xlab =''Tipped or not'', ylab =''Counts'');  
       dev.off();  
       OutputDataSet <- data.frame(data=readBin(file(image_file, "rb"), what=raw(), n=1e6));  
       ',  
       @input_data_1 = @query  
       WITH RESULT SETS ((plot varbinary(max)));  
    END  
    GO  
  
    ```  
  
    N’oubliez pas de modifier le code pour utiliser le nom de table approprié, si nécessaire.  
  
    -   La variable `@query` définit le texte de requête (`'SELECT tipped FROM nyctaxi_sample'`), qui est transmis au script R comme argument de la variable d’entrée du script, `@input_data_1`.  
  
    -   Le script R est assez simple : une variable R (`image_file`) est définie pour stocker l’image, puis la fonction `rxHistogram` est appelée pour générer le tracé.  
  
    -   Le périphérique R est défini sur **off**.  
  
        En R, quand vous émettez une commande principale de traçage, R ouvre une fenêtre graphique appelée *device* (périphérique). Vous pouvez modifier la taille, les couleurs et d’autres aspects de la fenêtre, ou vous pouvez désactiver le périphérique si vous écrivez dans un fichier ou si vous gérez la sortie d’une autre manière.  
  
    -   L’objet graphique R est sérialisé en data.frame R pour la sortie. Il s’agit d’une solution de contournement temporaire pour CTP3.  
  
##### Pour sortir des données varbinary dans un fichier graphique visible  
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], exécutez la commande suivante :  
  
    ```  
    EXEC [dbo].[PlotHistogram]  
    ```  
  
**Résultats**  
  
*traçage*  
*0xFFD8FFE000104A4649...*  
  
2.  Ouvrez une invite de commandes PowerShell et exécutez la commande suivante, en fournissant le nom d’instance, le nom de base de données, le nom d’utilisateur et les informations d’identification appropriés en tant qu’arguments :  
  
    ```  
    bcp "exec PlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  <database name>  -U <user name> -P <password>  
  
    ```  
  
    > [!NOTE]  
    > Les commutateurs de commande **bcp** respectent la casse.  
  
3.  Si la connexion réussit, vous serez invité à entrer davantage d’informations sur le format du fichier graphique. Appuyez sur Entrée à chaque invite pour accepter les valeurs par défaut, à l’exception de ces modifications :  
  
    -   Pour **prefix-length of field plot**, tapez 0.  
  
    -   Type **Y** si vous souhaitez enregistrer les paramètres de sortie pour une réutilisation ultérieure.  
  
    ```  
    Enter the file storage type of field plot [varbinary(max)]:  
    Enter prefix-length of field plot [8]: 0  
    Enter length of field plot [0]:  
    Enter field terminator [none]:  
  
    Do you want to save this format information in a file? [Y/n]  
    Host filename [bcp.fmt]:  
  
    ```  
  
**Résultats**  
  
*Démarrage de la copie...*  
*1 lignes copiées.*  
*Taille du paquet réseau (octets) : 4096*  
*Temps Horloge (ms.) total     : 3922   moy : (0.25 lignes par sec.)*  
   
> [!TIP]  
 > Si vous enregistrez les informations de format dans un fichier (bcp.fmt), l’utilitaire **bcp** génère une définition de format que vous pouvez appliquer ultérieurement à des commandes similaires sans avoir à entrer d’options de format de fichier graphique. Pour utiliser le fichier de format, ajoutez `-f bcp.fmt` à la fin d’une ligne de commande, après l’argument de mot de passe.  
  
4.  Le fichier de sortie est créé dans le même répertoire que celui où vous avez exécuté la commande PowerShell. Pour afficher le tracé, il suffit d’ouvrir le fichier plot.jpg.  
  
    ![taxi trips with and without tips](../../advanced-analytics/r-services/media/rsql-devtut-tippedornot.jpg "taxi trips with and without tips")  
  
### Enregistrement de tracés dans des fichiers (jpg, pdf) sur le serveur  
Sortir un tracé R dans un type de données binaire peut être pratique pour la consommation par les applications, mais cela n’est pas très utile à un spécialiste des données qui a besoin du tracé rendu pendant la phase d’exploration des données. En général, le spécialiste des données génère plusieurs visualisations de données, pour obtenir des informations sur les données de différentes perspectives.  
  
Pour générer des graphiques plus faciles à afficher, vous pouvez utiliser une procédure stockée qui crée la sortie de R dans des formats courants tels que .JPG, .PDF et .PNG. Une fois que la procédure stockée a créé le graphique, il vous suffit d’ouvrir le fichier pour visualiser le tracé.  
  
Lors de cette étape, vous allez créer une procédure stockée, _PlotInOutputFiles_, qui illustre comment utiliser des fonctions de traçage R pour créer des histogrammes, des nuages de points et autres au format .JPG et .PDF. Les fichiers graphiques sont enregistrés dans des fichiers locaux, autrement dit dans un dossier sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
##### Pour créer la procédure stockée PlotInOutputFiles  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez une nouvelle fenêtre de requête et collez l’instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante.  
  
    ```  
    CREATE PROCEDURE [dbo].[PlotInOutputFiles]  
    AS  
    BEGIN  
      SET NOCOUNT ON;  
      DECLARE @query nvarchar(max) =  
      N'SELECT cast(tipped as int) as tipped, tip_amount, fare_amount FROM [dbo].[nyctaxi_sample]'  
      EXECUTE sp_execute_external_script @language = N'R',  
      @script = N'  
       # Set output directory for files and check for existing files with same names   
        mainDir <- ''C:\\temp\\plots''  
        dir.create(mainDir, recursive = TRUE, showWarnings = FALSE)  
        setwd(mainDir);  
        print("Creating output plot files:", quote=FALSE)  
  
        # Open a jpeg file and output histogram of tipped variable in that file.  
        dest_filename = tempfile(pattern = ''rHistogram_Tipped_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.jpg'',sep="")  
        print(dest_filename, quote=FALSE);  
        jpeg(filename=dest_filename);  
        hist(InputDataSet$tipped, col = ''lightgreen'', xlab=''Tipped'',   
            ylab = ''Counts'', main = ''Histogram, Tipped'');  
         dev.off();  
           
        # Open a pdf file and output histograms of tip amount and fare amount.   
        # Outputs two plots in one row  
        dest_filename = tempfile(pattern = ''rHistograms_Tip_and_Fare_Amount_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.pdf'',sep="")  
        print(dest_filename, quote=FALSE);  
        pdf(file=dest_filename, height=4, width=7);  
        par(mfrow=c(1,2));  
        hist(InputDataSet$tip_amount, col = ''lightgreen'',   
            xlab=''Tip amount ($)'',   
            ylab = ''Counts'',   
            main = ''Histogram, Tip amount'', xlim = c(0,40), 100);  
        hist(InputDataSet$fare_amount, col = ''lightgreen'',   
            xlab=''Fare amount ($)'',   
            ylab = ''Counts'',   
            main = ''Histogram,   
            Fare amount'',   
            xlim = c(0,100), 100);  
       dev.off();  
  
        # Open a pdf file and output an xyplot of tip amount vs. fare amount using lattice;  
        # Only 10,000 sampled observations are plotted here, otherwise file is large.  
        dest_filename = tempfile(pattern = ''rXYPlots_Tip_vs_Fare_Amount_'', tmpdir = mainDir)  
        dest_filename = paste(dest_filename, ''.pdf'',sep="")  
        print(dest_filename, quote=FALSE);  
        pdf(file=dest_filename, height=4, width=4);  
        plot(tip_amount ~ fare_amount,   
            data = InputDataSet[sample(nrow(InputDataSet), 10000), ],   
            ylim = c(0,50),   
            xlim = c(0,150),   
            cex=.5,   
            pch=19,   
            col=''darkgreen'',    
            main = ''Tip amount by Fare amount'',   
            xlab=''Fare Amount ($)'',   
            ylab = ''Tip Amount ($)'');   
        dev.off();',  
     @input_data_1 = @query  
     END  
  
    ```  
  
    -   Le résultat de la requête SELECT dans la procédure stockée est stocké dans la trame de données R par défaut, `InputDataSet`. Vous pouvez ensuite appeler différentes fonctions de traçage R pour générer les fichiers graphiques proprement dits.  
  
        La plupart du script R incorporé représente des options pour ces fonctions graphiques, telles que `plot` ou `hist`.  
  
    -   Tous les fichiers sont enregistrés dans le dossier local _C:\temp\Plots\\_.  
  
        Le dossier de destination est défini par les arguments fournis au script R dans le cadre de la procédure stockée.  Vous pouvez modifier le dossier de destination en modifiant la valeur de la variable `mainDir`.  
  
2.  Exécutez l’instruction pour créer la procédure stockée.  
  
  
##### Pour générer les fichiers graphiques  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], exécutez la requête SQL suivante :  
  
    ```  
    EXEC PlotInOutputFiles  
  
    ```  
  
**Résultats**  
  
*Message(s) STDOUT provenant du script externe :*  
*[1] Création des fichiers de tracés de sortie :[1]* *C:\\\temp\\\plots\\\rHistogram_Tipped_18887f6265d4.jpg[1]* *C:\\\temp\\\plots\\\rHistograms_Tip_and_Fare_Amount_1888441e542c.pdf[1]* *C:\\\temp\\\plots\\\rXYPlots_Tip_vs_Fare_Amount_18887c9d517b.pdf*  
  
2.  Ouvrez le dossier de destination et examinez les fichiers qui ont été créés par le code R dans la procédure stockée. (Les nombres dans les noms de fichiers sont générés de façon aléatoire.)  
  
*  rHistogram_Tipped_*nnnn*.jpg : indique le nombre de trajets avec pourboire (1) par rapport au nombre de trajets sans pourboire (0). Cet histogramme ressemble beaucoup à celui que vous avez généré à l’étape précédente.  
  
*  rHistograms_Tip_and_Fare_Amount_*nnnn*.pdf : montre la distribution des valeurs dans les colonnes tip_amount et fare_amount.  
  
        ![histogram showing tip_amount and fare_amount](../../advanced-analytics/r-services/media/rsql-devtut-tipamtfareamt.PNG "histogram showing tip_amount and fare_amount")  
  
*  rXYPlots_Tip_vs_Fare_Amount_*nnnn*.pdf : nuage de points avec le prix sur l’axe des abscisses et le montant du pourboire sur l’axe y.  
  
        ![tip amount plotted over fare amount](../../advanced-analytics/r-services/media/rsql-devtut-tipamtbyfareamt.PNG "tip amount plotted over fare amount")  
  
3.  Pour exporter les fichiers vers un autre dossier, modifiez la valeur de la variable `mainDir` dans le script R incorporé dans la procédure stockée.  
  
    Vous pouvez également modifier le script pour générer des formats différents, plusieurs fichiers, et ainsi de suite.  
  
## Étape suivante  
[Étape 4 : Créer des fonctionnalités de données à l’aide de T-SQL](../../advanced-analytics/r-services/step-4-create-data-features-using-t-sql-in-database-advanced-analytics-tutorial.md)  
  
## Étape précédente  
[Étape 2 : Importer des données dans SQL Server à l’aide de PowerShell](../../advanced-analytics/r-services/step-2-import-data-to-sql-server-using-powershell.md)  
  
## Voir aussi  
[Analytique avancée en base de données pour les développeurs SQL &#40;Didacticiel&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
[Didacticiels pour SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
