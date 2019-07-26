---
title: Leçon 1 Explorer et visualiser les données à l’aide de Python et de T-SQL
description: Didacticiel illustrant comment incorporer python dans SQL Server procédures stockées et les fonctions T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/01/2018
ms.topic: tutorial
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0442fd942f0dd509f24b98b5ca1c6d6c31a197f0
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470558"
---
# <a name="explore-and-visualize-the-data"></a>Explorez et Visualisez les données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article fait partie d’un didacticiel, [l’analytique Python en base de données pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md). 

Dans cette étape, vous explorez les exemples de données et générez des tracés. Plus tard, vous allez apprendre à sérialiser des objets Graphics dans Python, puis à désérialiser ces objets et à créer des tracés.

## <a name="review-the-data"></a>Examiner les données

Tout d’abord, prenez une minute pour parcourir le schéma de données, car nous avons apporté des modifications pour faciliter l’utilisation des données relatives aux taxis de New York.

+ Le jeu de données d’origine a utilisé des fichiers distincts pour les identificateurs de taxi et les enregistrements de voyage. Nous avons joint les deux jeux de données d’origine sur les colonnes _Medallion_, _hack_license_et _pickup_datetime_.  
+ Le jeu de données d’origine répartie de nombreux fichiers et était assez volumineux. Nous avons sous-échantillonné pour avoir seulement 1% du nombre d’enregistrements d’origine. La table de données actuelle contient 1 703 957 lignes et 23 colonnes.

**Identificateurs de taxis**

La colonne _Medallion_ représente le numéro d’identification unique du taxi.

La colonne _hack_license_ contient le numéro de licence du pilote de taxi (rendu anonyme).

**Enregistrements de trajets et de prix**

Chaque enregistrement de trajet comprend les lieux de prise en charge et de dépose, ainsi que la durée et la distance du trajet.

Chaque enregistrement de prix inclut des informations telles que le type de paiement, le montant total du paiement et le montant du pourboire.

Les trois dernières colonnes peuvent être utilisées pour différentes tâches d’apprentissage automatique.  La colonne _tip_amount_ contient des valeurs numériques continues et peut être utilisée comme colonne **étiquette** pour l’analyse de régression. La colonne _tipped_ contient seulement des valeurs oui/non. Elle sert à la classification binaire. La colonne _tip_class_ a plusieurs **étiquettes de classes** , et peut donc être utilisée comme étiquette pour les tâches de classification multiclasse.

Les valeurs utilisées pour les colonnes d’étiquette sont toutes basées sur `tip_amount` la colonne, à l’aide des règles d’entreprise suivantes:

+ La colonne `tipped` d’étiquette contient les valeurs possibles 0 et 1

    Si `tip_amount` > 0, `tipped` = 1; sinon `tipped` = 0

+ La colonne `tip_class` d’étiquette contient des valeurs de classe possibles 0-4

    Classe 0: `tip_amount` = $0

    Classe 1: `tip_amount` > $0 et `tip_amount` < = $5
    
    Classe 2: `tip_amount` > $5 et `tip_amount` < = $10
    
    Classe 3: `tip_amount` > $10 et `tip_amount` < = $20
    
    Classe 4: `tip_amount` > $20

## <a name="create-plots-using-python-in-t-sql"></a>Créer des tracés à l’aide de Python dans T-SQL

Le développement d’une solution de science des données comprend généralement l’exploration et la visualisation des données. Étant donné que la visualisation est un outil puissant pour comprendre la distribution des données et des valeurs hors norme, Python fournit de nombreux packages pour la visualisation des données. Le module **matplotlib** est l’une des bibliothèques les plus populaires pour la visualisation et comprend de nombreuses fonctions permettant de créer des histogrammes, des nuages de points, des surfaces et d’autres graphiques d’exploration de données.

Dans cette section, vous allez apprendre à utiliser des tracés à l’aide de procédures stockées. Au lieu d’ouvrir l’image sur le serveur, vous stockez l' `plot` objet Python en tant que données **varbinary** , puis vous l’écrivez dans un fichier qui peut être partagé ou affiché ailleurs.

### <a name="create-a-plot-as-varbinary-data"></a>Créer un tracé en tant que données varbinary

La procédure stockée retourne un objet python `figure` sérialisé sous la forme d’un flux de données **varbinary** . Vous ne pouvez pas afficher les données binaires directement, mais vous pouvez utiliser le code Python sur le client pour désérialiser et afficher les figures, puis enregistrer le fichier image sur un ordinateur client.

1. Créez la procédure stockée **PyPlotMatplotlib**, si le script PowerShell ne l’a pas encore fait.

    - La variable `@query` définit le texte `SELECT tipped FROM nyctaxi_sample`de la requête, qui est passé au bloc de code Python en tant qu’argument de la variable `@input_data_1`d’entrée de script,.
    - Le script Python est assez simple: les objets **matplotlib** `figure` sont utilisés pour créer l’histogramme et le nuage de points, et ces objets sont ensuite sérialisés à l’aide de la `pickle` bibliothèque.
    - L’objet Graphics Python est sérialisé en un  tableau pandas pour la sortie.
  
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

2. À présent, exécutez la procédure stockée sans arguments pour générer un tracé à partir des données codées en dur en tant que requête d’entrée.

    ```sql
    EXEC [dbo].[PyPlotMatplotlib]
    ```

3. Les résultats doivent ressembler à ceci:
  
    ```sql
    plot
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    0xFFD8FFE000104A4649...
    ```

  
4. À partir d’un [client python](../python/setup-python-client-tools-sql.md), vous pouvez maintenant vous connecter à l’instance SQL Server qui a généré les objets de tracé binaire et afficher les tracés. 

    Pour ce faire, exécutez le code python suivant, en remplaçant le nom du serveur, le nom de la base de données et les informations d’identification comme il convient. Assurez-vous que la version Python est la même sur le client et sur le serveur. Assurez-vous également que les bibliothèques Python sur votre client (telles que matplotlib) sont de la même version ou d’une version supérieure par rapport aux bibliothèques installées sur le serveur.
  
    **Utilisation de l’authentification SQL Server:**
    
    ```python
    %matplotlib notebook
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER=SQL Server;SERVER={SERVER_NAME};DATABASE={DB_NAME};UID={USER_NAME};PWD={PASSWORD}')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[PyPlotMatplotlib]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

    **Utilisation de l’authentification Windows:**

    ```python
    %matplotlib notebook
    import pyodbc
    import pickle
    import os
    cnxn = pyodbc.connect('DRIVER=SQL Server;SERVER={SERVER_NAME};DATABASE={DB_NAME};Trusted_Connection=True;')
    cursor = cnxn.cursor()
    cursor.execute("EXECUTE [dbo].[PyPlotMatplotlib]")
    tables = cursor.fetchall()
    for i in range(0, len(tables)):
        fig = pickle.loads(tables[i][0])
        fig.savefig(str(i)+'.png')
    print("The plots are saved in directory: ",os.getcwd())
    ```

5.  Si la connexion réussit, un message semblable à celui-ci doit s’afficher:
  
    *Les tracés sont enregistrés dans le répertoire: xxxx*
  
6.  Le fichier de sortie est créé dans le répertoire de travail Python. Pour afficher le tracé, localisez le répertoire de travail Python, puis ouvrez le fichier. L’illustration suivante montre un tracé enregistré sur l’ordinateur client.
  
    ![Montant du pourboire vs montant] de la course (media/sqldev-python-sample-plot.png "Montant du pourboire vs montant") de la course 

## <a name="next-step"></a>Étape suivante

[Créer des caractéristiques de données à l’aide de T-SQL](sqldev-py5-train-and-save-a-model-using-t-sql.md)

## <a name="previous-step"></a>Étape précédente

[Télécharger le jeu de données des taxis de New York](demo-data-nyctaxi-in-sql.md)

