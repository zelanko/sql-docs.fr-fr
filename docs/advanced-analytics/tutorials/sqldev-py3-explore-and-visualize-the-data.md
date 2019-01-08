---
title: Leçon 1 Explorer et visualiser des données à l’aide de Python et T-SQL - SQL Server Machine Learning
description: Didacticiel montrant comment intégrer Python dans SQL Server des procédures stockées et fonctions T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: e92b2e1a5d4d5e1ad6990ffafa1a1cfcfbb9d806
ms.sourcegitcommit: ee76332b6119ef89549ee9d641d002b9cabf20d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53645338"
---
# <a name="explore-and-visualize-the-data"></a>Explorer et visualiser les données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Cet article fait partie d’un didacticiel, [analytique en base de données Python pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md). 

Dans cette étape, vous allez explorer les exemples de données et générer des tracés. Plus tard, vous allez apprendre à sérialiser des objets graphics dans Python, puis désérialiser ces objets et rendre les tracés.

## <a name="review-the-data"></a>Passez en revue les données

Tout d’abord, prenez une minute pour parcourir le schéma de données, comme nous avons apporté des changements pour le rendre plus facile à utiliser les données NYC Taxi

+ Le jeu de données d’origine utilisé des fichiers distincts pour les identificateurs de taxis et les enregistrements de trajets. Nous avons joint deux jeux de données d’origine sur les colonnes _medallion_, _hack_license_, et _pickup_datetime_.  
+ Le jeu de données d’origine sur lesquelles s’étend de nombreux fichiers et a été très volumineux. Nous avons sous-échantillonnée pour obtenir seulement 1 % du nombre d’enregistrements d’origine. La table de données actuelle comporte 1 703 957 lignes et 23 colonnes.

**Identificateurs de taxis**

Le _medallion_ colonne représente le numéro d’identification unique du taxi.

Le _hack_license_ colonne contient le numéro de licence du conducteur du taxi (anonyme).

**Enregistrements de trajets et de prix**

Chaque enregistrement de trajet comprend les lieux de prise en charge et de dépose, ainsi que la durée et la distance du trajet.

Chaque enregistrement de prix inclut des informations telles que le type de paiement, le montant total du paiement et le montant du pourboire.

Les trois dernières colonnes peuvent être utilisées pour différentes tâches d’apprentissage automatique.  La colonne _tip_amount_ contient des valeurs numériques continues et peut être utilisée comme colonne **étiquette** pour l’analyse de régression. La colonne _tipped_ contient seulement des valeurs oui/non. Elle sert à la classification binaire. La colonne _tip_class_ a plusieurs **étiquettes de classes** , et peut donc être utilisée comme étiquette pour les tâches de classification multiclasse.

Les valeurs utilisées pour les colonnes d’étiquette sont toutes basées sur la `tip_amount` colonne, à l’aide de ces règles d’entreprise :

+ Colonne d’étiquette `tipped` a des valeurs possibles, 0 et 1

    Si `tip_amount` > 0, `tipped` = 1 ; sinon `tipped` = 0

+ Colonne d’étiquette `tip_class` a des valeurs possibles de classe 0 et 4

    Classe 0 : `tip_amount` = 0 $

    Classe 1 : `tip_amount` > de 0 $ et `tip_amount` < = 5 $
    
    Classe 2 : `tip_amount` > à 5 $ et `tip_amount` < = 10 $
    
    Classe 3 : `tip_amount` > $10 et `tip_amount` < = 20 $
    
    Classe 4 : `tip_amount` > 20

## <a name="create-plots-using-python-in-t-sql"></a>Créer des tracés à l’aide de Python dans T-SQL

Le développement d’une solution de science des données comprend généralement l’exploration et la visualisation des données. Visualisation étant un outil puissant pour comprendre la distribution des données et des valeurs hors norme, Python fournit de nombreux packages de visualisation de données. Le **matplotlib** module est une des bibliothèques plus populaires pour la visualisation et inclut de nombreuses fonctions pour créer des histogrammes et nuages de points, tracés de la boîte et autres graphiques d’exploration de données.

Dans cette section, vous allez apprendre à travailler avec des tracés à l’aide de procédures stockées. Au lieu d’ouvrir l’image sur le serveur, vous stockez l’objet Python `plot` comme **varbinary** données, puis écrire que dans un fichier qui peut être partagé ou affichés ailleurs.

### <a name="create-a-plot-as-varbinary-data"></a>Créer un tracé en tant que données varbinary

La procédure stockée retourne un Python sérialisée `figure` objet en tant que flux de **varbinary** données. Vous ne pouvez pas afficher directement les données binaires, mais vous pouvez utiliser le code Python sur le client à désérialiser et d’afficher les chiffres et puis enregistrez le fichier image sur un ordinateur client.

1. Créer la procédure stockée **PyPlotMatplotlib**, si le script PowerShell s’est pas déjà fait.

    - La variable `@query` définit le texte de requête `SELECT tipped FROM nyctaxi_sample`, qui est transmis au bloc de code Python comme argument à la variable d’entrée de script, `@input_data_1`.
    - Le script Python est relativement simple : **matplotlib** `figure` objets sont utilisés pour tracer le graphique histogramme et à nuages de points, et ces objets sont sérialisés à l’aide de la `pickle` bibliothèque.
    - L’objet graphics de Python est sérialisée vers un **pandas** trame de données pour la sortie.
  
    ```sql
    DROP PROCEDURE IF EXISTS PyPlotMatplotlib;
    GO

    CREATE PROCEDURE [dbo].[PyPlotMatplotlib]
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

2. Maintenant, exécutez la procédure stockée sans arguments pour générer un graphique à partir des données codées en dur en tant que la requête d’entrée.

    ```sql
    EXEC [dbo].[PyPlotMatplotlib]
    ```

3. Les résultats doivent être quelque chose comme ceci :
  
    ```sql
    plot
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    ```

  
4. À partir d’un [client Python](../python/setup-python-client-tools-sql.md), vous pouvez maintenant vous connecter à l’instance de SQL Server qui a généré les objets de traçage binaire et afficher les tracés. 

    Pour ce faire, exécutez le code Python suivant, en remplaçant le nom du serveur, nom de la base de données et les informations d’identification comme il convient. Vérifiez que la version de Python est le même sur le client et le serveur. Assurez-vous également que les bibliothèques Python sur votre client (par exemple, matplotlib) utilisent la version identique ou supérieure par rapport aux bibliothèques installées sur le serveur.
  
    **À l’aide de l’authentification SQL Server :**
    
    ```python
    %matplotlib notebook
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER={SERVER_NAME};DATABASE={DB_NAME};UID={USER_NAME};PWD={PASSWORD}')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[PyPlotMatplotlib]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

    **À l’aide de l’authentification Windows :**

    ```python
    %matplotlib notebook
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER={SERVER_NAME};DATABASE={DB_NAME};Trusted_Connection=True;')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[PyPlotMatplotlib]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

5.  Si la connexion est établie, vous devez voir un message semblable au suivant :
  
    *Les tracés sont enregistrés dans le répertoire : xxxx*
  
6.  Le fichier de sortie est créé dans le répertoire de travail Python. Pour afficher le tracé, recherchez le répertoire de travail Python et ouvrez le fichier. L’illustration suivante montre un tracé enregistré sur l’ordinateur client.
  
    ![Quantité vs Fare montant du pourboire](media/sqldev-python-sample-plot.png "montant du pourboire quantité et prix") 

## <a name="next-step"></a>Étape suivante

[Créer des caractéristiques de données à l’aide de T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Étape précédente

[Télécharger le jeu de données NYC Taxi](demo-data-nyctaxi-in-sql.md)

