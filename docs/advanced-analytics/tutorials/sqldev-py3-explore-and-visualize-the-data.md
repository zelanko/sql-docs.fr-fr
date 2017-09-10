---
title: "Étape 3 : explorer et visualiser les données | Microsoft Docs"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-python
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dfb80fcd3241b22f0ac72c2cf4cd8a18d1add857
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="step-3-explore-and-visualize-the-data"></a>Étape 3 : Explorer et visualiser les données

Le développement d’une solution de science des données comprend généralement l’exploration et la visualisation des données. Dans cette étape, vous allez explorer les exemples de données et générer des graphiques. Une version ultérieure, vous allez apprendre à sérialiser des objets graphics dans Python, puis désérialiser ces objets et rendre des graphiques.

> [!NOTE]
> Cette procédure pas à pas ne montre que la tâche de classification binaire ; vous êtes invité à réessayer de générer des modèles distincts pour les autres tâches d’apprentissage deux, régression et classification multiclasse.

## <a name="review-the-data"></a>Examiner les données

Dans le dataset d’origine, les identificateurs de taxis et les enregistrements de trajets ont été fournis dans des fichiers distincts. Toutefois, pour simplifier l’utilisation des exemples de données, les deux datasets d’origine ont été joints sur les colonnes _medallion_, _hack_license_et _pickup_datetime_.  Les enregistrements ont aussi été échantillonnés pour obtenir seulement 1 % du nombre d’enregistrements d’origine. Le dataset échantillonné obtenu compte 1 703 957 lignes et 23 colonnes.

**Identificateurs de taxis**

- La colonne _medallion_ représente le numéro d’ID unique du taxi.
- La colonne _hack_license_ contient le numéro de licence du conducteur du taxi (anonyme).

**Enregistrements de trajets et de prix**

- Chaque enregistrement de trajet comprend les lieux de prise en charge et de dépose, ainsi que la durée et la distance du trajet.
- Chaque enregistrement de prix inclut des informations telles que le type de paiement, le montant total du paiement et le montant du pourboire.
- Les trois dernières colonnes peuvent être utilisées pour différentes tâches d’apprentissage automatique.  La colonne _tip_amount_ contient des valeurs numériques continues et peut être utilisée comme colonne **étiquette** pour l’analyse de régression. La colonne _tipped_ contient seulement des valeurs oui/non. Elle sert à la classification binaire. La colonne _tip_class_ a plusieurs **étiquettes de classes** , et peut donc être utilisée comme étiquette pour les tâches de classification multiclasse.
- Les valeurs utilisées pour les colonnes d’étiquettes sont basées sur la colonne _tip_amount_ , à l’aide de ces règles d’entreprise :
  
    |Nom de la colonne dérivée|Règle|
    |-|-|
     |tipped|Si tip_amount > 0, tipped = 1, sinon tipped = 0|
    |tip_class|Classe 0 : tip_amount = 0 $<br /><br />Classe 1 : tip_amount > 0 $ et tip_amount <= 5 $<br /><br />Classe 2 : tip_amount > 5 $ et tip_amount <= 10 $<br /><br />Classe 3 : tip_amount > 10 $ et tip_amount <= 20 $<br /><br />Classe 4 : tip_amount > 20 $|

## <a name="create-plots-using-python-in-t-sql"></a>Créer des graphiques à l’aide de Python dans T-SQL

Étant donné que la visualisation est un outil puissant permettant de comprendre la distribution des données et des valeurs hors norme, Python fournit de nombreux packages de visualisation de données. Le **matplotlib** module est une bibliothèque populaire qui inclut de nombreuses fonctions pour la création d’histogrammes, nuages de points, des graphiques de zone et autres graphiques d’exploration de données.

Dans cette section, vous allez apprendre comment utiliser des graphiques à l’aide de procédures stockées. Vous allez stocker les `plot` Python de l’objet en un **varbinary** données tapez et enregistrez les graphiques générés sur le serveur.

### <a name="storing-plots-as-varbinary-data-type"></a>Stockage de tracés en tant que type de données varbinary

Le **revoscalepy** module inclus avec SQL Server 2017 Machine Learning Services contient les bibliothèques analogues aux bibliothèques R dans le package RevoScaleR. Dans cet exemple, vous allez utiliser l’équivalent de Python de `rxHistogram` pour tracer un histogramme basé sur des données d’une [!INCLUDE[tsql](../../includes/tsql-md.md)] requête. Pour simplifier, vous l’encapsule dans une procédure stockée, _PlotHistogram_.

La procédure stockée retourne une Python sérialisée `figure` objet sous forme de flux de **varbinary** données. Vous ne pouvez pas afficher directement les données binaires, mais vous pouvez utiliser du code Python à désérialiser et afficher les chiffres sur le client et puis enregistrez le fichier image sur un ordinateur client.

### <a name="create-the-stored-procedure-plotspython"></a>Créez la procédure stockée Plots_Python

1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], ouvrez une nouvelle **requête** fenêtre.

2.  Sélectionnez la base de données pour la procédure pas à pas, puis créez la procédure à l’aide de cette instruction. N’oubliez pas de modifier le code pour utiliser le nom de table approprié, si nécessaire.
  
    ```SQL
    
    CREATE PROCEDURE [dbo].[SerializePlots]
    AS
    BEGIN
      SET NOCOUNT ON;
      DECLARE @query nvarchar(max) =
      N'SELECT cast(tipped as int) as tipped, tip_amount, fare_amount FROM [dbo].[nyctaxi_sample]'
      EXECUTE sp_execute_external_script
      @language = N'Python',
      @script = N'
    import matplotlib
    matplotlib.use("Agg")
    import matplotlib.pyplot as plt
    import pandas as pd
    import pickle

    fig_handle = plt.figure()
    plt.hist(InputDataSet.tipped)
    plt.xlabel("Tipped")
    plt.ylabel("Counts")
    plt.title("Histogram, Tipped")
    plot0 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.hist(InputDataSet.tip_amount)
    plt.xlabel("Tip amount ($)")
    plt.ylabel("Counts")
    plt.title("Histogram, Tip amount")
    plot1 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.hist(InputDataSet.fare_amount)
    plt.xlabel("Fare amount ($)")
    plt.ylabel("Counts")
    plt.title("Histogram, Fare amount")
    plot2 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    plt.scatter( InputDataSet.fare_amount, InputDataSet.tip_amount)
    plt.xlabel("Fare Amount ($)")
    plt.ylabel("Tip Amount ($)")
    plt.title("Tip amount by Fare amount")
    plot3 = pd.DataFrame(data =[pickle.dumps(fig_handle)], columns =["plot"])
    plt.clf()

    OutputDataSet = plot0.append(plot1, ignore_index=True).append(plot2, ignore_index=True).append(plot3, ignore_index=True)
    ',
                                     @input_data_1 = @query
      WITH RESULT SETS ((plot varbinary(max)))
    END

    GO
  
    ```
**Remarques :**

- La variable `@query` définit le texte de requête (`'SELECT tipped FROM nyctaxi_sample'`), qui est passé au bloc de code Python comme argument à la variable d’entrée du script, `@input_data_1`.
- Le script Python est relativement simple : **matplotlib** `figure` objets sont utilisés pour effectuer le traçage de l’histogramme et à nuages de points, et ces objets sont sérialisés puis à l’aide de la `pickle` bibliothèque.
- L’objet graphics Python est sérialisée vers un Python **pandas** trame de données pour la sortie.

### <a name="output-varbinary-data-to-viewable-graphics-file"></a>Données varbinary de sortie à un fichier graphique visible

1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], exécutez la commande suivante :
  
    ```
    EXEC [dbo].[SerializePlots]
    ```
  
    **Résultats**
  
    *traçage*
    *0xFFD8FFE000104A4649... * 
     *0xFFD8FFE000104A4649... * 
     *0xFFD8FFE000104A4649... * 
     *0xFFD8FFE000104A4649...*

  
2.  Sur l’ordinateur client, exécutez le code Python suivant, en remplaçant le nom du serveur, nom de la base de données et les informations d’identification comme il convient.
  
    **Pour l’authentification SQL server :**
    
        ```python
        import pyodbc
        import pickle
        import os
        cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER={SERVER_NAME};DATABASE={DB_NAME};UID={USER_NAME};PWD={PASSOWRD}')
        cursor = cnxn.cursor()
        cursor.execute("EXECUTE [dbo].[SerializePlots]")
        tables = cursor.fetchall()
        for i in range(0, len(tables)):
            fig = pickle.loads(tables[i][0])
            fig.savefig(str(i)+'.png')
        print("The plots are saved in directory: ",os.getcwd())
        ```  
    **Pour l’authentification Windows :**

        ```python
        import pyodbc
        import pickle
        import os
        cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER={SERVER_NAME};DATABASE={DB_NAME};Trusted_Connection=yes;')
        cursor = cnxn.cursor()
        cursor.execute("EXECUTE [dbo].[SerializePlots]")
        tables = cursor.fetchall()
        for i in range(0, len(tables)):
            fig = pickle.loads(tables[i][0])
            fig.savefig(str(i)+'.png')
        print("The plots are saved in directory: ",os.getcwd())
        ```

    > [!NOTE]
    > Assurez-vous que la version Python est le même sur le client et le serveur. En outre, assurez-vous que les bibliothèques de Python que vous utilisez sur votre client (par exemple, matplotlib) sont de la version identique ou ultérieure par rapport aux bibliothèques sont installées sur le serveur.


3.  Si la connexion est établie, vous voyez les résultats ci-dessous
  
    *Les graphiques sont enregistrés dans le répertoire : xxxx*
  
4.  Le fichier de sortie sera créé dans le répertoire de travail Python. Pour afficher le tracé, ouvrez simplement le répertoire de travail Python. L’illustration suivante montre un exemple de tracé enregistré sur l’ordinateur client.
  
    ![Conseil le montant de frais vs](media/sqldev-python-sample-plot.png "Conseil, montant de frais de vs") 

## <a name="next-step"></a>Étape suivante

[Étape 4 : Créer des fonctionnalités de données à l’aide de T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Étape précédente

[Étape 2 : Importer des données dans SQL Server à l’aide de PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="see-also"></a>Voir aussi

[Machine Learning Services avec Python](../python/sql-server-python-services.md)

