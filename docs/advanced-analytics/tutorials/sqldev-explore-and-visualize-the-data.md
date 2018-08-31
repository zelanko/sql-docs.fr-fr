---
title: Leçon 3 Explorer et visualiser des données à l’aide de R et T-SQL (SQL Server Machine Learning) | Microsoft Docs
description: Didacticiel expliquant comment incorporer R dans SQL Server des procédures stockées et fonctions T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6b34de3c71629a1563bf0d480306680dc6253748
ms.sourcegitcommit: 320958d0f55b6974abf46f8a04f7a020ff86a0ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42703622"
---
# <a name="lesson-3-explore-and-visualize-the-data"></a>Leçon 3 : Explorer et visualiser les données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fait partie d’un didacticiel pour les développeurs SQL sur l’utilisation de R dans SQL Server.

Dans cette leçon, vous passez en revue les exemples de données et puis générer des tracés à l’aide de [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram) de [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler) et générique [hist.](https://www.rdocumentation.org/packages/graphics/versions/3.5.0/topics/hist) fonction dans r de base. Ces fonctions R sont déjà incluses dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].

Un objectif clé est montrant comment appeler des fonctions R à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)] dans les procédures stockées et enregistrez les résultats dans des formats de fichier d’application :

+ Créer une procédure stockée à l’aide **RxHistogram** pour générer un tracé R en tant que données varbinary. Utilisez **bcp** pour exporter le flux binaire dans un fichier image.
+ Créer une procédure stockée à l’aide **hist.** pour générer un graphique, l’enregistrement des résultats en tant que sortie JPG et PDF.

> [!NOTE]
> Visualisation étant un outil puissant pour comprendre la forme de données et la distribution, R fournit un éventail de fonctions et des packages pour générer des histogrammes, nuages de points, les tracés de zone et autres graphiques d’exploration de données. R crée généralement des images à l’aide d’un périphérique R pour une sortie graphique, vous pouvez capturer et stocker en tant qu’un **varbinary** type de données pour le rendu dans une application. Vous pouvez également enregistrer les images à l’un des formats de fichier prise en charge (. JPG. PDF, etc.).

## <a name="review-the-data"></a>Passez en revue les données

Le développement d’une solution de science des données comprend généralement l’exploration et la visualisation des données. Tout d’abord prendre une minute pour examiner les exemples de données, si vous n’avez pas déjà.

Dans le dataset d’origine, les identificateurs de taxis et les enregistrements de trajets ont été fournis dans des fichiers distincts. Toutefois, pour faciliter les exemples de données à utiliser, les deux jeux de données d’origine ont été joints sur les colonnes _medallion_, _hack\_licence_, et _pickup\_ date/heure_.  Les enregistrements ont aussi été échantillonnés pour obtenir seulement 1 % du nombre d’enregistrements d’origine. Le dataset échantillonné obtenu compte 1 703 957 lignes et 23 colonnes.

**Identificateurs de taxis**
  
-   La colonne _medallion_ représente le numéro d’ID unique du taxi.
  
-   Le _hack\_licence_ colonne contient le numéro de licence du conducteur du taxi (anonyme).
  
**Enregistrements de trajets et de prix**
  
-   Chaque enregistrement de trajet comprend les lieux de prise en charge et de dépose, ainsi que la durée et la distance du trajet.
  
-   Chaque enregistrement de prix inclut des informations telles que le type de paiement, le montant total du paiement et le montant du pourboire.
  
-   Les trois dernières colonnes peuvent être utilisées pour différentes tâches d’apprentissage automatique. Le _Conseil\_quantité_ colonne contient des valeurs numériques continues et peut être utilisée comme le **étiquette** colonne pour l’analyse de régression. La colonne _tipped_ contient seulement des valeurs oui/non. Elle sert à la classification binaire. Le _Conseil\_classe_ colonne comporte plusieurs **classe étiquettes** et par conséquent être utilisé comme étiquette pour les tâches de classification multiclasse.
  
    Cette procédure pas à pas ne montre que la tâche de classification binaire. Si vous le souhaitez, vous pouvez essayer de créer des modèles pour les autres deux tâches d’apprentissage automatique, la régression et la classification multiclasse.
  
-   Les valeurs utilisées pour les colonnes d’étiquette sont toutes basées sur le _Conseil\_quantité_ colonne, à l’aide de ces règles d’entreprise :
  
    |Nom de la colonne dérivée|Règle|
    |-|-|
     |tipped|Si tip_amount > 0, tipped = 1, sinon tipped = 0|
    |tip_class|Classe 0 : tip_amount = 0 $<br /><br />Classe 1 : tip_amount > 0 $ et tip_amount <= 5 $<br /><br />Classe 2 : tip_amount > 5 $ et tip_amount <= 10 $<br /><br />Classe 3 : tip_amount > 10 $ et tip_amount <= 20 $<br /><br />Classe 4 : tip_amount > 20 $|

## <a name="create-a-stored-procedure-using-rxhistogram-to-plot-the-data"></a>Créer une procédure stockée à l’aide de rxHistogram pour tracer les données

Pour créer le tracé, utilisez [rxHistogram](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxhistogram), une des fonctions R améliorées fournies dans [RevoScaleR](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/revoscaler). Cette étape trace un histogramme basé sur les données à partir d’un [!INCLUDE[tsql](../../includes/tsql-md.md)] requête. Vous pouvez encapsuler cette fonction dans une procédure stockée, **PlotHistogram**.

1. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans l’Explorateur d’objets, cliquez sur le **NYCTaxi_Sample** de base de données, développez **programmabilité**, puis développez **Stored Procedures** pour afficher le procédures créées dans la leçon 2.

2. Avec le bouton droit **PlotHistogram** et sélectionnez **modifier** pour afficher la source. Vous pouvez exécuter cette procédure pour appeler **rxHistogram** sur les données contenues dans la colonne tipped de nyctaxi_sample table.

3. Si vous le souhaitez, comme un exercice d’apprentissage, créez votre propre copie de cette procédure stockée à l’aide de l’exemple suivant. Ouvrez une nouvelle fenêtre de requête et collez le script suivant pour créer une procédure stockée qui trace l’histogramme. Cet exemple se nomme **PlotHistogram2** afin d’éviter les conflits de dénomination avec la procédure préexistante.

    ```SQL
    CREATE PROCEDURE [dbo].[PlotHistogram2]
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

La procédure stockée **PlotHistogram2** est identique à une procédure stockée préexistante **PlotHistogram** créé par le `RunSQL_SQL_Walkthrough.ps1` script. 
  
+ La variable `@query` définit le texte de requête (`'SELECT tipped FROM nyctaxi_sample'`), qui est transmis au script R comme argument de la variable d’entrée du script, `@input_data_1`.
  
+ Le script R est assez simple : une variable R (`image_file`) est définie pour stocker l’image, puis le **rxHistogram** fonction est appelée pour générer le tracé.
  
+ Le périphérique R est défini sur **hors** étant donné que vous exécutez cette commande comme un script externe dans SQL Server. En général, dans R, lorsque vous émettez une commande de traçage de haut niveau, R ouvre une fenêtre graphique, appelée un *appareil*. Vous pouvez modifier la taille, les couleurs et d’autres aspects de la fenêtre, ou vous pouvez désactiver le périphérique si vous écrivez dans un fichier ou si vous gérez la sortie d’une autre manière.
  
+ L’objet graphique R est sérialisé en data.frame R pour la sortie.

### <a name="execute-the-stored-procedure-and-use-bcp-to-export-binary-data-to-an-image-file"></a>Exécutez la procédure stockée et l’utilisation de bcp pour exporter des données binaires dans un fichier image

La procédure stockée retourne l’image sous forme de flux de données varbinary qui, évidemment, ne peut pas être affiché directement. Toutefois, vous pouvez utiliser l’utilitaire **bcp** pour obtenir les données varbinary et les enregistrer en tant que fichier image sur un ordinateur client.
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], exécutez la commande suivante :
  
    ```SQL
    EXEC [dbo].[PlotHistogram]
    ```
  
    **Résultats**
    
    *traçage*
    *0xFFD8FFE000104A4649...*
  
2.  Ouvrez une invite de commande PowerShell et exécutez la commande suivante, en fournissant le nom d’instance approprié, nom de la base de données, nom d’utilisateur et les informations d’identification en tant qu’arguments. Pour ceux qui utilisent des identités de Windows, vous pouvez remplacer **- U** et **-P** avec **-T**.
  
     ```text
     bcp "exec PlotHistogram" queryout "plot.jpg" -S <SQL Server instance name> -d  TaxiNYC_Sample  -U <user name> -P <password>
     ```

    > [!NOTE]
    > Commutateurs de commande pour bcp respectent la casse.
  
3.  Si la connexion réussit, vous serez invité à entrer davantage d’informations sur le format du fichier graphique. 

   Appuyez sur Entrée à chaque invite pour accepter les valeurs par défaut, à l’exception de ces modifications :
    
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
    
    ```
    Starting copy...
    1 rows copied.
    Network packet size (bytes): 4096
    Clock Time (ms.) Total     : 3922   Average : (0.25 rows per sec.)
    ```

    > [!TIP]
    > Si vous enregistrez les informations de format dans un fichier (bcp.fmt), l’utilitaire **bcp** génère une définition de format que vous pouvez appliquer ultérieurement à des commandes similaires sans avoir à entrer d’options de format de fichier graphique. Pour utiliser le fichier de format, ajoutez `-f bcp.fmt` à la fin d’une ligne de commande, après l’argument de mot de passe.
  
4.  Le fichier de sortie est créé dans le même répertoire que celui où vous avez exécuté la commande PowerShell. Pour afficher le tracé, il suffit d’ouvrir le fichier plot.jpg.
  
    ![courses de taxi avec et sans pourboires](media/rsql-devtut-tippedornot.jpg "courses de taxi avec et sans pourboires")  
  
## <a name="create-a-stored-procedure-using-hist-and-multiple-output-formats"></a>Créer une procédure stockée à l’aide d’historique et plusieurs formats de sortie

En règle générale, les scientifiques des données génèrent plusieurs visualisations de données pour obtenir des informations sur les données à partir de différentes perspectives. Dans cet exemple, la procédure stockée utilise la fonction de l’historique pour créer l’histogramme, exportation des données binaires vers des formats courants tels que. JPG. PDF, et. PNG. 

1. Utilisez la procédure stockée existante, **PlotInOutputFiles**, pour écrire des histogrammes et nuages de points pour les autres graphiques R. JPG et. Format PDF. Le `RunSQL_SQL_Walkthrough.ps1` crée **PlotInOutputFiles** et l’ajoute à la base de données. Utiliser avec le bouton droit **modifier** pour afficher la source.

2. Si vous le souhaitez, comme un exercice d’apprentissage, créer votre propre copie de la procédure en tant que **PlotInOutputFiles2**, avec un nom unique pour éviter tout conflit d’affectation de noms.

    Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez une nouvelle **requête** fenêtre et la coller dans le code suivant [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction.
  
    ```SQL
    CREATE PROCEDURE [dbo].[PlotInOutputFiles2]  
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
  
+ Tous les fichiers sont enregistrés dans le dossier local _C:\temp\Plots\\_. Le dossier de destination est défini par les arguments fournis au script R dans le cadre de la procédure stockée.  Vous pouvez modifier le dossier de destination en modifiant la valeur de la variable `mainDir`.

+ Pour exporter les fichiers vers un autre dossier, modifiez la valeur de la variable `mainDir` dans le script R incorporé dans la procédure stockée. Vous pouvez également modifier le script pour générer des formats différents, plusieurs fichiers, et ainsi de suite.

### <a name="execute-the-stored-procedure"></a>Exécuter la procédure stockée

Exécutez l’instruction suivante pour exporter les binaires de tracer les données aux formats de fichier JPEG et PDF.

```SQL
EXEC PlotInOutputFiles
```

**Résultats**
    
```
STDOUT message(s) from external script:
[1] Creating output plot files:[1] C:\temp\plots\rHistogram_Tipped_18887f6265d4.jpg[1] 

C:\temp\plots\rHistograms_Tip_and_Fare_Amount_1888441e542c.pdf[1]

C:\temp\plots\rXYPlots_Tip_vs_Fare_Amount_18887c9d517b.pdf
```

Les nombres dans les noms de fichiers sont générés au hasard pour vous assurer que vous n’obtenez une erreur lorsque vous tentez d’écrire dans un fichier existant.

### <a name="view-output"></a>Affichage de la sortie 

Pour afficher le tracé, ouvrez le dossier de destination et examinez les fichiers qui ont été créés par le code R dans la procédure stockée.

1. Atteindre le dossier indiqué dans le message STDOUT (dans l’exemple, il s’agit de C:\temp\plots\)

2. Ouvrez `rHistogram_Tipped.jpg` pour afficher le nombre de trajets une info-bulle par rapport sans pourboire. (Cet histogramme est comme celui que vous avez généré à l’étape précédente).

3. Ouvrez `rHistograms_Tip_and_Fare_Amount.pdf` pour afficher la distribution des pourboires, tracée sur les montants de prix.
    
  ![Histogramme affichant tip_amount et fare_amount](media/rsql-devtut-tipamtfareamt.PNG "Histogramme affichant tip_amount et fare_amount")

4. Ouvrez `rXYPlots_Tip_vs_Fare_Amount.pdf` pour afficher un nuage de points avec le montant du trajet sur l’axe des abscisses et le montant du pourboire sur l’axe y.

   ![montant du pourboire tracées sur le montant](media/rsql-devtut-tipamtbyfareamt.PNG "montant du pourboire tracées sur le montant du trajet")

## <a name="next-lesson"></a>Leçon suivante

[Leçon 3 : Créer des fonctionnalités de données à l’aide de T-SQL](sqldev-create-data-features-using-t-sql.md)

## <a name="previous-lesson"></a>Leçon précédente

[Leçon 1 : Configurer les données de démonstration NYC Taxi](sqldev-download-the-sample-data.md)
