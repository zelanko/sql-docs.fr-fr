---
title: Leçon 1 Explorer et visualiser les données à l’aide de R et de T-SQL
description: Didacticiel illustrant l’exploration et la visualisation des données SQL Server à l’aide de fonctions R.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/29/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 2c204e06edd830d8036b6d0119ce1aff1a9c6833
ms.sourcegitcommit: 1c3f56deaa4c1ffbe5d7f75752ebe10447c3e7af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "68715371"
---
# <a name="lesson-1-explore-and-visualize-the-data"></a>Leçon 1 : Explorez et Visualisez les données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article fait partie d’un didacticiel pour les développeurs SQL sur l’utilisation de R dans SQL Server.

Dans cette étape, vous allez examiner les exemples de données, puis générer des tracés à l’aide de [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) à partir de [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) et de la fonction [Hist](https://www.rdocumentation.org/packages/graphics/versions/3.5.0/topics/hist) générique dans base R. Ces fonctions R sont déjà incluses dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

L’objectif principal de cette leçon est d’illustrer comment appeler des fonctions [!INCLUDE[tsql](../../includes/tsql-md.md)] R à partir de procédures stockées et enregistrer les résultats dans des formats de fichiers d’application:

+ Créez une procédure stockée à l’aide de **RxHistogram** pour générer un tracé R sous forme de données varbinary. Utilisez **BCP** pour exporter le flux binaire vers un fichier image.
+ Créez une procédure stockée à l’aide de la fonction **Hist** pour générer un tracé, en enregistrant les résultats au format jpg et PDF.

> [!NOTE]
> Étant donné que la visualisation est un outil puissant pour la compréhension de la forme et de la distribution des données, R propose une gamme de fonctions et de packages pour générer des histogrammes, des nuages de points, des surfaces et d’autres graphiques d’exploration de données. R crée généralement des images à l’aide d’un appareil R pour la sortie graphique, que vous pouvez capturer et stocker en tant que type de données **varbinary** pour le rendu dans l’application. Vous pouvez également enregistrer les images dans l’un des formats de fichiers de prise en charge (. JPG,. PDF, etc.).

## <a name="review-the-data"></a>Examiner les données

Le développement d’une solution de science des données comprend généralement l’exploration et la visualisation des données. Par conséquent, prenez une minute pour examiner les exemples de données, si vous ne l’avez pas déjà fait.

Dans le jeu de données public d’origine, les identificateurs et les enregistrements de trajet des taxis ont été fournis dans des fichiers distincts. Toutefois, pour faciliter l’utilisation des exemples de données, les deux jeux de données d’origine ont été joints aux colonnes _Medallion_, _hack\_License_et _pick\_DateTime_.  Les enregistrements ont aussi été échantillonnés pour obtenir seulement 1 % du nombre d’enregistrements d’origine. Le dataset échantillonné obtenu compte 1 703 957 lignes et 23 colonnes.

**Identificateurs de taxis**
  
-   La colonne _Medallion_ représente le numéro d’identification unique du taxi.
  
-   La colonne de _licence hack\__ contient le numéro de licence du pilote taxi (rendu anonyme).
  
**Enregistrements de trajets et de prix**
  
-   Chaque enregistrement de trajet comprend les lieux de prise en charge et de dépose, ainsi que la durée et la distance du trajet.
  
-   Chaque enregistrement de prix inclut des informations telles que le type de paiement, le montant total du paiement et le montant du pourboire.
  
-   Les trois dernières colonnes peuvent être utilisées pour différentes tâches d’apprentissage automatique. La _colonne\_montant du pourboire_ contient des valeurs numériques continues et peut être utilisée comme colonne d' **étiquette** pour l’analyse de régression. La colonne _tipped_ contient seulement des valeurs oui/non. Elle sert à la classification binaire. La colonne de _classe\_Tip_ contient plusieurs **étiquettes de classe** et peut donc être utilisée comme étiquette pour les tâches de classification multiclasse.
  
    Cette procédure pas à pas ne montre que la tâche de classification binaire. Si vous le souhaitez, vous pouvez essayer de créer des modèles pour les autres deux tâches d’apprentissage automatique, la régression et la classification multiclasse.
  
-   Les valeurs utilisées pour les colonnes d’étiquette sont toutes basées sur la colonne du _montant\__ des pourboires, à l’aide des règles d’entreprise suivantes:
  
    |Nom de la colonne dérivée|Règle|
    |-|-|
     |tipped|Si tip_amount > 0, tipped = 1, sinon tipped = 0|
    |tip_class|Classe 0 : tip_amount = 0 $<br /><br />Classe 1 : tip_amount > 0 $ et tip_amount <= 5 $<br /><br />Classe 2 : tip_amount > 5 $ et tip_amount <= 10 $<br /><br />Classe 3 : tip_amount > 10 $ et tip_amount <= 20 $<br /><br />Classe 4 : tip_amount > 20 $|

## <a name="create-a-stored-procedure-using-rxhistogram-to-plot-the-data"></a>Créer une procédure stockée à l’aide de rxHistogram pour tracer les données

Pour créer le tracé, utilisez [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram), l’une des fonctions R améliorées fournies dans [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler). Cette étape trace un histogramme basé sur les données d' [!INCLUDE[tsql](../../includes/tsql-md.md)] une requête. Vous pouvez encapsuler cette fonction dans une procédure stockée, **PlotRxHistogram**.

1. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l’Explorateur d’objets, cliquez avec le bouton droit sur la base de données **NYCTaxi_Sample** et sélectionnez **nouvelle requête**.

2. Collez le script suivant pour créer une procédure stockée qui trace l’histogramme. Cet exemple est nommé **RPlotRxHistogram*.

    ```sql
    CREATE PROCEDURE [dbo].[RxPlotHistogram]
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

Les points clés à comprendre dans ce script sont les suivants: 
  
+ La variable `@query` définit le texte de requête (`'SELECT tipped FROM nyctaxi_sample'`), qui est transmis au script R comme argument de la variable d’entrée du script, `@input_data_1`. Pour les scripts R qui s’exécutent en tant que processus externes, vous devez disposer d’un mappage un-à-un entre les entrées de votre script et les entrées de la procédure stockée système [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) qui démarre la session R sur SQL Server.
  
+ Dans le script R, une variable (`image_file`) est définie pour stocker l’image. 

+ La fonction **rxHistogram** de la bibliothèque RevoScaleR est appelée pour générer le tracé.
  
+ L’appareil R a la valeur **off** , car vous exécutez cette commande en tant que script externe dans SQL Server. En général, dans R, lorsque vous émettez une commande de traçage de haut niveau, R ouvre une fenêtre graphique, appelée *appareil*. Vous pouvez désactiver l’appareil si vous écrivez dans un fichier ou si vous gérez la sortie d’une autre façon.
  
+ L’objet graphique R est sérialisé en data.frame R pour la sortie.

### <a name="execute-the-stored-procedure-and-use-bcp-to-export-binary-data-to-an-image-file"></a>Exécuter la procédure stockée et utiliser BCP pour exporter des données binaires dans un fichier image

La procédure stockée retourne l’image sous forme de flux de données varbinary qui, évidemment, ne peut pas être affiché directement. Toutefois, vous pouvez utiliser l’utilitaire **bcp** pour obtenir les données varbinary et les enregistrer en tant que fichier image sur un ordinateur client.
  
1. Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], exécutez la commande suivante :
  
    ```sql
    EXEC [dbo].[RxPlotHistogram]
    ```
  
    **Résultats**
    
    *tracé* *0xFFD8FFE000104A4649...*
  
2. Ouvrez une invite de commandes PowerShell et exécutez la commande suivante, en indiquant le nom de l’instance, le nom de la base de données, le nom d’utilisateur et les informations d’identification appropriés comme arguments. Pour ceux qui utilisent des identités Windows, vous pouvez remplacer **-U** et **-P** par **-T**.
  
    ```powershell
    bcp "exec RxPlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  NYCTaxi_Sample  -U <user name> -P <password> -T
    ```

    > [!NOTE]
    > Les commutateurs de commande pour BCP respectent la casse.
  
3. Si la connexion réussit, vous serez invité à entrer davantage d’informations sur le format du fichier graphique. 

   Appuyez sur Entrée à chaque invite pour accepter les valeurs par défaut, à l’exception de ces modifications :
    
   + Pour **prefix-length of field plot**, tapez 0.
  
   + Type **Y** si vous souhaitez enregistrer les paramètres de sortie pour une réutilisation ultérieure.
  
    ```powershell
    Enter the file storage type of field plot [varbinary(max)]: 
    Enter prefix-length of field plot [8]: 0
    Enter length of field plot [0]:
    Enter field terminator [none]:
  
    Do you want to save this format information in a file? [Y/n]
    Host filename [bcp.fmt]:
    ```
  
    **Résultats**
    
    ```powershell
    Starting copy...
    1 rows copied.
    Network packet size (bytes): 4096
    Clock Time (ms.) Total     : 3922   Average : (0.25 rows per sec.)
    ```

    > [!TIP]
    > Si vous enregistrez les informations de format dans un fichier (bcp.fmt), l’utilitaire **bcp** génère une définition de format que vous pouvez appliquer ultérieurement à des commandes similaires sans avoir à entrer d’options de format de fichier graphique. Pour utiliser le fichier de format, ajoutez `-f bcp.fmt` à la fin d’une ligne de commande, après l’argument de mot de passe.
  
4.  Le fichier de sortie est créé dans le même répertoire que celui où vous avez exécuté la commande PowerShell. Pour afficher le tracé, il suffit d’ouvrir le fichier plot.jpg.
  
    ![courses de taxi avec et sans pourboires](media/rsql-devtut-tippedornot.jpg "courses de taxi avec et sans pourboires")  
  
## <a name="create-a-stored-procedure-using-hist-and-multiple-output-formats"></a>Créer une procédure stockée à l’aide de l’historique et de plusieurs formats de sortie

En règle générale, les scientifiques des données génèrent plusieurs visualisations de données pour obtenir des informations sur les données à partir de différentes perspectives. Dans cet exemple, vous allez créer une procédure stockée appelée **RPlotHist** pour écrire des histogrammes, des nuages et d’autres graphiques R. JPG et. Format PDF.

Cette procédure stockée utilise la fonction **Hist** pour créer l’histogramme, en exportant les données binaires dans des formats populaires tels que. JPG,. PDF et. Format. 

1. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l’Explorateur d’objets, cliquez avec le bouton droit sur la base de données **NYCTaxi_Sample** et sélectionnez **nouvelle requête**.

2. Collez le script suivant pour créer une procédure stockée qui trace l’histogramme. Cet exemple est appelé **RPlotHist** .
  
    ```sql
    CREATE PROCEDURE [dbo].[RPlotHist]  
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
  
+ Le résultat de la requête SELECT dans la procédure stockée est stocké dans la trame de données R par défaut, `InputDataSet`. Vous pouvez ensuite appeler différentes fonctions de traçage R pour générer les fichiers graphiques proprement dits. La plupart du script R incorporé représente des options pour ces fonctions graphiques, telles que `plot` ou `hist`.
  
+ Tous les fichiers sont enregistrés dans le dossier local C:\temp\Plots. Le dossier de destination est défini par les arguments fournis au script R dans le cadre de la procédure stockée.  Vous pouvez modifier le dossier de destination en modifiant la valeur de la variable `mainDir`.

+ Pour exporter les fichiers vers un autre dossier, modifiez la valeur de la variable `mainDir` dans le script R incorporé dans la procédure stockée. Vous pouvez également modifier le script pour générer des formats différents, plusieurs fichiers, et ainsi de suite.

### <a name="execute-the-stored-procedure"></a>Exécuter la procédure stockée

Exécutez l’instruction suivante pour exporter des données de tracé binaires au format de fichier JPEG et PDF.

```sql
EXEC RPlotHist
```

**Résultats**
    
```sql
STDOUT message(s) from external script:
[1] Creating output plot files:[1] C:\temp\plots\rHistogram_Tipped_18887f6265d4.jpg[1] 

C:\temp\plots\rHistograms_Tip_and_Fare_Amount_1888441e542c.pdf[1]

C:\temp\plots\rXYPlots_Tip_vs_Fare_Amount_18887c9d517b.pdf
```

Les nombres dans les noms de fichiers sont générés de manière aléatoire pour s’assurer que vous ne recevez pas d’erreur lors de la tentative d’écriture dans un fichier existant.

### <a name="view-output"></a>Afficher la sortie 

Pour afficher le tracé, ouvrez le dossier de destination et passez en revue les fichiers qui ont été créés par le code R dans la procédure stockée.

1. Accédez au dossier indiqué dans le message STDOUT (dans l’exemple, il s’agit de C:\temp\plots\)

2. Ouvrez `rHistogram_Tipped.jpg` pour afficher le nombre de voyages qui ont reçu un Conseil et les voyages qui n’ont pas eu de Conseil. (Cet histogramme est semblable à celui que vous avez généré à l’étape précédente.)

3. Ouvrir `rHistograms_Tip_and_Fare_Amount.pdf` pour afficher la répartition des montants des pourboires, en fonction des montants des prix.
    
  ![histogramme présentant tip_amount et fare_amount](media/rsql-devtut-tipamtfareamt.PNG "histogramme présentant tip_amount et fare_amount")

4. Ouvrez `rXYPlots_Tip_vs_Fare_Amount.pdf` pour afficher un nuage avec le montant du prix sur l’axe des abscisses et le montant du pourboire sur l’axe des y.

   ![montant du pourboire tracé sur le montant du tarif](media/rsql-devtut-tipamtbyfareamt.PNG "montant du pourboire tracé sur le montant du tarif")

## <a name="next-lesson"></a>Leçon suivante

[Leçon 2 : Créer des fonctionnalités de données à l’aide de T-SQL](sqldev-create-data-features-using-t-sql.md)

## <a name="previous-lesson"></a>Leçon précédente

[Configurer les données de démonstration des taxis de New York](demo-data-nyctaxi-in-sql.md)
