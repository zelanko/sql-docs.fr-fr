---
title: Exécutez l’Assistant Migration des données à partir de la ligne de commande (SQL Server) | Microsoft Docs
description: Découvrez comment exécuter l’Assistant Migration des données à partir de la ligne de commande pour évaluer les bases de données SQL Server pour la migration
ms.custom: ''
ms.date: 09/01/2017
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Command Line
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 6b364dc03d48cbc1c0487362712e10f7ab0b782e
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/04/2018
ms.locfileid: "37785460"
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>Exécutez l’Assistant Migration des données à partir de la ligne de commande
Avec la version 2.1 et versions ultérieures, lorsque vous installez Data Migration Assistant, il installe également dmacmd.exe dans *% ProgramFiles%\\Microsoft Data Migration Assistant\\*. Utilisez dmacmd.exe pour évaluer vos bases de données en mode sans assistance et renvoyer le résultat au fichier JSON ou CSV. Cette méthode est particulièrement utile lors de l’évaluation de plusieurs bases de données ou des bases de données énormes. 

> [!NOTE]
> Dmacmd.exe prend en charge uniquement les évaluations en cours d’exécution. Migrations ne sont pas prises en charge pour l’instant.


## <a name="command-line-arguments"></a>Arguments de ligne de commande

```
DmaCmd.exe /AssessmentName="string"
/AssessmentDatabases="connectionString1" \["connectionString2"\]
\[/AssessmentTargetPlatform="TargetPlatform"\]
/AssessmentEvaluateRecommendations|/AssessmentEvaluateCompatibilityIssues
\[/AssessmentOverwriteResult\]
/AssessmentResultJson="file"|/AssessmentResultCsv="file"
```


|Argument  |Description  | Requis (Y/N)
|---------|---------|---------------|
| `/help or /?`     | Comment utiliser le texte d’aide dmacmd.exe        | N
|`/AssessmentName`     |   Nom du projet d’évaluation   | O
|`/AssessmentDatabases`     | Liste délimitée par des chaînes de connexion. Nom de la base de données (catalogue Initial) respecte la casse. | O
|`/AssessmentTargetPlatform`     | Plateforme cible pour l’évaluation, les valeurs prises en charge : SqlServer2012, SqlServer2014, SqlServer2016 et AzureSqlDatabaseV12. Valeur par défaut est SqlServer2016   | N
|`/AssessmentEvaluateFeatureParity`  | Exécuter des règles de parité de fonctionnalité  | N
|`/AssessmentEvaluateCompatibilityIssues`     | Exécuter les règles de compatibilité  | O <br> (AssessmentEvaluateCompatibilityIssues ou AssessmentEvaluateRecommendations est requises.)
|`/AssessmentEvaluateRecommendations`     | Exécuter les recommandations de fonctionnalité        | O <br> (AssessmentEvaluateCompatibilityIssues ou AssessmentEvaluateRecommendationsis requis)
|`/AssessmentOverwriteResult`     | Remplacer le fichier de résultat    | N
|`/AssessmentResultJson`     | Chemin d’accès complet au fichier de résultat JSON     | O <br> (AssessmentResultJson ou AssessmentResultCsv est requis)
|`/AssessmentResultCsv`    | Chemin d’accès complet au fichier CSV   | O <br>(AssessmentResultJson ou AssessmentResultCsv est requis)




## <a name="examples"></a>Exemples

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Évaluation de bases de données unique à l’aide de règles de compatibilité de l’authentification et en cours d’exécution Windows**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***Integrated Security=true*"**
***/AssessmentEvaluateCompatibilityIssues*** /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```



**Évaluation de la base de données unique à l’aide de la recommandation de fonctionnalité d’authentification et en cours d’exécution de SQL Server**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;***User Id=myUsername;Password=myPassword;***"
***/AssessmentEvaluateRecommendations*** /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```


**Évaluation de base de données unique pour la plateforme cible SQL Server 2012, enregistrer les résultats dans le fichier .json et .csv**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
***/AssessmentTargetPlatform="SqlServer2012"***
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
***/AssessmentResultJson***="C:\\temp\\Results\\AssessmentReport.json"
***/AssessmentResultCsv***="C:\\temp\\Results\\AssessmentReport.csv"
```


**Évaluation de la base de données unique pour la plateforme cible de base de données SQL Azure, enregistrez les résultats dans un fichier .json et .csv**

```
DmaCmd.exe /AssessmentName="TestAssessment" 
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentTargetPlatform="AzureSqlDatabaseV12"
/AssessmentEvaluateCompatibilityIssues /AssessmentEvaluateFeatureParity
/AssessmentOverwriteResult 
/AssessmentResultCsv="C:\\temp\\AssessmentReport.csv" 
/AssessmentResultJson="C:\\temp\\AssessmentReport.json"
```


**Évaluation de plusieurs bases de données**

```
DmaCmd.exe /AssessmentName="TestAssessment"
***/AssessmentDatabases="Server=SQLServerInstanceName1;Initial
Catalog=DatabaseName1;Integrated Security=true"
"Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated
Security=true" "Server=SQLServerInstanceName2;Initial
Catalog=DatabaseName3;Integrated Security=true"***
/AssessmentTargetPlatform="SqlServer2016"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
/AssessmentResultJson="C:\\Results\\test2016.json"
```



## <a name="see-also"></a>Voir aussi

[Télécharger l’Assistant de Migration de données](https://www.microsoft.com/download/details.aspx?id=53595)
