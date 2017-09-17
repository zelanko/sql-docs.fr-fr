---
title: "Étape 1 : Télécharger les exemples de données | Documents Microsoft"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
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
ms.openlocfilehash: 147860e9af8cce86d1a7ccbd3e53f20d240fcd49
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="step-1-download-the-sample-data"></a>Étape 1 : Télécharger les exemples de données

Dans cette étape, vous allez télécharger l’exemple de dataset et les scripts. Les données et les fichiers de script sont partagés sur Github, mais le script PowerShell télécharge les fichiers de script et de données dans le répertoire local de votre choix.

## <a name="download-the-data-and-scripts"></a>Télécharger les données et les scripts

1. Ouvrez une console de commande Windows PowerShell.

    Utilisez l’option, **exécuter en tant qu’administrateur**, si des privilèges d’administrateur sont nécessaires pour créer le répertoire de destination ou pour écrire des fichiers vers la destination spécifiée.

2. Exécutez les commandes PowerShell suivantes, en définissant la valeur du paramètre *DestDir* sur un répertoire local.  La valeur par défaut, nous avons utilisé ici est **TempPythonSQL**.

    ```
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/PythonSQL/Download_Scripts_SQL_Walkthrough.ps1'
    $ps1_dest = "$pwd\Download_Scripts_SQL_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir 'C:\tempPythonSQL'
    ```
    
    Si le dossier que vous spécifiez dans *DestDir* n’existe pas, il est créé par le script PowerShell.
    
    Si vous obtenez une erreur, vous pouvez temporairement définir la stratégie d’exécution des scripts PowerShell pour **illimitée** uniquement pour cette procédure pas à pas, à l’aide de la **contournement** argument et les modifications apportées à la session active de portée. L’exécution de cette commande n’a pas d’incidence sur la configuration.
    
    `Set\-ExecutionPolicy Bypass \-Scope Process`

3. Selon votre connexion Internet, le téléchargement peut prendre un certain temps. Une fois tous les fichiers téléchargés, le script PowerShell s’ouvre sur le dossier spécifié par  *DestDir*. Dans l’invite de commandes PowerShell, exécutez la commande suivante et examinez les fichiers qui ont été téléchargés.

    ```
    ls
    ```
**Résultats :**

![liste des fichiers téléchargés par le script PowerShell](media/sqldev-python-filelist.png "liste des fichiers téléchargés par le script PowerShell")

## <a name="next-step"></a>Étape suivante

[Étape 2 : Importer des données dans SQL Server à l’aide de PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="previous-step"></a>Étape précédente

[Dans base de données Analytique de Python pour le développeur SQL](sqldev-in-database-python-for-sql-developers.md)

## <a name="see-also"></a>Voir aussi

[Machine Learning Services avec Python](../python/sql-server-python-services.md)



