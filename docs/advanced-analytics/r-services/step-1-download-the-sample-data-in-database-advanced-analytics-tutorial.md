---
title: "&#201;tape 1 : T&#233;l&#233;charger les exemples de donn&#233;es (Didacticiel sur l’analytique avanc&#233;e en base de donn&#233;es) | Microsoft Docs"
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
ms.assetid: 32a5d5ad-c58a-4669-a90d-ef296b48fcd8
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# &#201;tape 1 : T&#233;l&#233;charger les exemples de donn&#233;es (Didacticiel sur l’analytique avanc&#233;e en base de donn&#233;es)
Dans cette étape, vous allez télécharger l’exemple de dataset et les fichiers de script [!INCLUDE[tsql](../../includes/tsql-md.md)] qui sont utilisés dans cette procédure pas à pas. Les données et les fichiers de script sont partagés sur Github, mais le script PowerShell télécharge les fichiers de script et de données dans le répertoire local de votre choix.  
  
## Télécharger les données et les scripts  
  
1.  Ouvrez une console de commande Windows PowerShell.  
  
    Utilisez l’option **Exécuter en tant qu’administrateur**, si des privilèges d’administrateur sont nécessaires pour créer le répertoire de destination ou pour écrire des fichiers dans la destination spécifiée.  
  
2.  Exécutez les commandes PowerShell suivantes, en définissant la valeur du paramètre *DestDir* sur un répertoire local.  La valeur par défaut que nous avons utilisée ici est **TempRSQL**.  
  
    ```  
    $source = ‘https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_SQL_Walkthrough.ps1’  
    $ps1_dest = “$pwd\Download_Scripts_SQL_Walkthrough.ps1”  
    $wc = New-Object System.Net.WebClient  
    $wc.DownloadFile($source, $ps1_dest)  
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir ‘C:\tempRSQL’  
  
    ```  
  
    Si le dossier que vous spécifiez dans *DestDir* n’existe pas, il est créé par le script PowerShell.  
  
    > [!TIP]  
    > Si vous obtenez une erreur, vous pouvez temporairement définir la stratégie d’exécution des scripts PowerShell sur **illimitée** uniquement pour cette procédure pas à pas, en utilisant l’argument Bypass et en limitant l’étendue des modifications à la session actuelle.  
    >   
    >````  
    > Set\-ExecutionPolicy Bypass \-Scope Process  
    >````   
    > L’exécution de cette commande n’a pas d’incidence sur la configuration.  
  
    Selon votre connexion Internet, le téléchargement peut prendre un certain temps.  
  
3.  Une fois tous les fichiers téléchargés, le script PowerShell s’ouvre sur le dossier spécifié par *DestDir*. Dans l’invite de commandes PowerShell, exécutez la commande suivante et examinez les fichiers qui ont été téléchargés.  
  
    ```  
    ls  
    ```  
  
    **Résultats :**  
  
    ![list of files downloaded by PowerShell script](../../advanced-analytics/r-services/media/rsql-devtut-filelist.PNG "list of files downloaded by PowerShell script")  
  
## Étape suivante  
[Étape 2 : Importer des données dans SQL Server à l’aide de PowerShell](../../advanced-analytics/r-services/step-2-import-data-to-sql-server-using-powershell.md)  
  
## Étape précédente  
[Analytique avancée en base de données pour les développeurs SQL &#40;Didacticiel&#41;](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
  
## Voir aussi  
[Didacticiels pour SQL Server R Services](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  
