---
title: "Étape 1 : Télécharger les exemples de données | Documents Microsoft"
ms.custom: 
ms.date: 10/17/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to: SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: "2"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: b2ac1eeb53ba9f9a0dcbf86ee772db9c8b2d3553
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="step-1-download-the-sample-data"></a>Étape 1 : Télécharger les exemples de données

Cet article fait partie d’un didacticiel, [analytique Python de la base de données pour les développeurs SQL](sqldev-in-database-python-for-sql-developers.md). 

Les données et les scripts de ce didacticiel sont partagés sur Github. Dans cette étape, vous utilisez un script PowerShell pour télécharger les fichiers de script et de données dans un répertoire local de votre choix.

## <a name="run-the-script"></a>Exécutez le script

1. Ouvrez une console de commande Windows PowerShell.

    Utilisez l’option, **exécuter en tant qu’administrateur**, si des privilèges d’administrateur sont nécessaires pour créer le répertoire de destination ou pour écrire des fichiers vers la destination spécifiée.

2. Exécutez les commandes PowerShell suivantes, en définissant la valeur du paramètre *DestDir* sur un répertoire local.  La valeur par défaut, nous avons utilisé ici est `C:\temp\pysql`.

    ```ps
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/PythonSQL/Download_Scripts_SQL_Walkthrough.ps1'
    $ps1_dest = "$pwd\Download_Scripts_SQL_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir 'C:\temp\pysql'
    ```
    
    Si le dossier que vous spécifiez dans *DestDir* n’existe pas, il est créé par le script PowerShell.
    
    Si vous obtenez une erreur, définissez temporairement la stratégie d’exécution des scripts PowerShell pour **illimitée** pour cette procédure pas à pas, à l’aide de la **contournement** argument et les modifications apportées à la session active de portée. L’exécution de cette commande n’a pas d’incidence sur la configuration.
    
    ```ps
    Set-ExecutionPolicy Bypass -Scope Process
    ```

3. En fonction de votre connexion internet, le téléchargement peut prendre un certain temps. 

## <a name="view-the-results"></a>Afficher les résultats

Une fois tous les fichiers téléchargés, le script PowerShell s’ouvre sur le dossier spécifié par  *DestDir*. 

+ Dans l’invite de commandes PowerShell, exécutez la commande suivante, pour répertorier les fichiers qui ont été téléchargés.

    ```ps
    ls
    ```

![liste des fichiers téléchargés par le script PowerShell](media/sqldev-python-filelist.png "liste des fichiers téléchargés par le script PowerShell")

## <a name="next-step"></a>Étape suivante

[Étape 2 : Importer des données dans SQL Server à l’aide de PowerShell](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="previous-step"></a>Étape précédente

[Dans base de données Analytique de Python pour le développeur SQL](sqldev-in-database-python-for-sql-developers.md)

## <a name="see-also"></a>Voir aussi

[Machine Learning Services avec Python](../python/sql-server-python-services.md)


