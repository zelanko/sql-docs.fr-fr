---
title: Exécuter Assistant Migration de données à partir de la ligne de commande
description: Découvrez comment exécuter Assistant Migration de données à partir de la ligne de commande pour évaluer SQL Server bases de données pour la migration
ms.custom: seo-lt-2019
ms.date: 05/06/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Command Line
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.openlocfilehash: 3fbf2429a384ad64b1b416e3920a193d92a6c387
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74056624"
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>Exécuter Assistant Migration de données à partir de la ligne de commande

Avec la version 2,1 et versions ultérieures, lorsque vous installez Assistant Migration de données, il installe également dmacmd. exe dans *% ProgramFiles%\\\\Assistant Migration de données Microsoft*. Utilisez dmacmd. exe pour évaluer vos bases de données en mode sans assistance et générer le résultat dans un fichier JSON ou CSV. Cette méthode est particulièrement utile lors de l’évaluation de plusieurs bases de données ou de bases de données volumineuses. 

> [!NOTE]
> Dmacmd. exe prend en charge l’exécution des évaluations uniquement. Les migrations ne sont pas prises en charge pour le moment.

## <a name="assessments-using-the-command-line-interface-cli"></a>Évaluations à l’aide de l’interface de ligne de commande (CLI)

```
DmaCmd.exe /AssessmentName="string"
/AssessmentDatabases="connectionString1" \["connectionString2"\]
\[/AssessmentSourcePlatform="SourcePlatform"]
\[/AssessmentTargetPlatform="TargetPlatform"\]
/AssessmentEvaluateRecommendations|/AssessmentEvaluateCompatibilityIssues
\[/AssessmentOverwriteResult\]
/AssessmentResultJson="file"|/AssessmentResultCsv="file"
```

|Argument  |Description  | Obligatoire (o/N)
|---------|---------|---------------|
| `/help or /?`     | Comment utiliser le texte d’aide de dmacmd. exe        | N
|`/AssessmentName`     |   Nom du projet d’évaluation   | O
|`/AssessmentDatabases`     | Liste de chaînes de connexion délimitée par des espaces. Le nom de la base de données (catalogue initial) respecte la casse. | O
|`/AssessmentSourcePlatform`     | Plateforme source pour l’évaluation : <br>Valeurs prises en charge pour l’évaluation : SqlOnPrem, RdsSqlServer (valeur par défaut) <br>Valeurs prises en charge pour l’évaluation de la disponibilité cible : SqlOnPrem, RdsSqlServer (par défaut), Cassandra (version préliminaire)   | N
|`/AssessmentTargetPlatform`     | Plateforme cible pour l’évaluation :  <br> Valeurs prises en charge pour l’évaluation : AzureSqlDatabase, ManagedSqlServer, SqlServer2012, SqlServer2014, SqlServer2016, SqlServerLinux2017 et SqlServerWindows2017 (par défaut)  <br> Valeurs prises en charge pour l’évaluation de la disponibilité cible : ManagedSqlServer (par défaut), CosmosDB (version préliminaire)   | N
|`/AssessmentEvaluateFeatureParity`  | Exécuter les règles de parité des fonctionnalités. Si la plateforme source est RdsSqlServer, l’évaluation de la parité des fonctionnalités n’est pas prise en charge pour la plateforme cible AzureSqlDatabase  | N
|`/AssessmentEvaluateCompatibilityIssues`     | Exécuter les règles de compatibilité  | O <br> (AssessmentEvaluateCompatibilityIssues ou AssessmentEvaluateRecommendations est requis.)
|`/AssessmentEvaluateRecommendations`     | Exécuter les recommandations relatives aux fonctionnalités        | O <br> (AssessmentEvaluateCompatibilityIssues ou AssessmentEvaluateRecommendations est requis)
|`/AssessmentOverwriteResult`     | Remplacer le fichier de résultats    | N
|`/AssessmentResultJson`     | Chemin d’accès complet au fichier de résultats JSON     | O <br> (AssessmentResultJson ou AssessmentResultCsv est requis)
|`/AssessmentResultCsv`    | Chemin d’accès complet au fichier de résultats CSV   | O <br> (AssessmentResultJson ou AssessmentResultCsv est requis)
|`/Action`    | Utilisez SkuRecommendation pour connaître les recommandations relatives aux références SKU, utilisez AssessTargetReadiness pour effectuer l’évaluation de la disponibilité cible.   | N
|`/SourceConnections`    | Liste de chaînes de connexion, délimitée par des espaces. Le nom de la base de données (catalogue initial) est facultatif. Si aucun nom de base de données n’est fourni, toutes les bases de données de la source sont évaluées.   | O <br> (Obligatoire si action est « AssessTargetReadiness »)
|`/TargetReadinessConfiguration`    | Chemin d’accès complet au fichier XML décrivant les valeurs pour le nom, les connexions source et le fichier de résultats.   | O <br> (TargetReadinessConfiguration ou SourceConnections est requis)
|`/FeatureDiscoveryReportJson`    | Chemin d’accès au rapport JSON de détection de fonctionnalités. Si ce fichier est généré, il peut être utilisé pour exécuter à nouveau l’évaluation de la disponibilité cible sans se connecter à la source. | N
|`/ImportFeatureDiscoveryReportJson`    | Chemin d’accès au rapport JSON de détection de fonctionnalités créé précédemment. Au lieu de connexions source, ce fichier sera utilisé.   | N

## <a name="examples-of-assessments-using-the-cli"></a>Exemples d’évaluations à l’aide de l’interface CLI

**Dmacmd. exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Évaluation de base de données unique à l’aide de l’authentification Windows et exécution des règles de compatibilité**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```

**Évaluation de base de données unique à l’aide de l’authentification SQL Server et de la recommandation d’exécution**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;User Id=myUsername;Password=myPassword;"
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```

**Évaluation de base de données unique pour la plateforme cible SQL Server 2012, enregistrer les résultats dans un fichier. JSON et. csv**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentTargetPlatform="SqlServer2012"
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```

**Évaluation de base de données unique pour la plateforme cible SQL Azure base de données, enregistrer les résultats dans un fichier. JSON et. csv**

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
/AssessmentDatabases="Server=SQLServerInstanceName1;Initial
Catalog=DatabaseName1;Integrated Security=true"
"Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated
Security=true" "Server=SQLServerInstanceName2;Initial
Catalog=DatabaseName3;Integrated Security=true"
/AssessmentTargetPlatform="SqlServer2016"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
/AssessmentResultJson="C:\\Results\\test2016.json"
```

**Évaluation de la préparation à la cible d’une base de données unique à l’aide de l’authentification Windows**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/SourceConnections="Server=SQLServerInstanceName;Initial Catalog=DatabaseName;Integrated Security=true" 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"
```

**Évaluation de la préparation à la cible d’une base de données unique à l’aide de l’authentification SQL Server**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/SourceConnections="Server=SQLServerInstanceName;Initial Catalog=DatabaseName;User Id=myUsername;Password=myPassword;" /AssessmentEvaluateRecommendations 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json" 

```

**Évaluation de base de données unique pour la plateforme cible SQL Azure base de données, enregistrer les résultats dans un fichier. JSON et. csv**

```
DmaCmd.exe /AssessmentName="TestAssessment" 
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentSourcePlatform="SqlOnPrem"
/AssessmentTargetPlatform="AzureSqlDatabase"
/AssessmentEvaluateCompatibilityIssues /AssessmentEvaluateFeatureParity
/AssessmentOverwriteResult 
/AssessmentResultCsv="C:\\temp\\AssessmentReport.csv" 
/AssessmentResultJson="C:\\temp\\AssessmentReport.json"

```

**Évaluation de la préparation à la cible de plusieurs bases de données**

```
DmaCmd.exe /Action=AssessTargetReadiness
/AssessmentName="TestAssessment"
/AssessmentSourcePlatform=SourcePlatform
/AssessmentTargetPlatform=TargetPlatform
/SourceConnections="Server=SQLServerInstanceName1;Initial Catalog=DatabaseName1;Integrated Security=true" "Server=SQLServerInstanceName1;Initial Catalog=DatabaseName2;Integrated Security=true" "Server=SQLServerInstanceName2;Initial Catalog=DatabaseName3;Integrated Security=true"
/AssessmentOverwriteResult  
/AssessmentResultJson="C:\Results\test2016.json"

(/AssessmentSourcePlatform and /AssessmentTargetPlatform are optional.)
```

**Évaluation de la disponibilité cible pour toutes les bases de données sur un serveur à l’aide de l’authentification Windows**

```
DmaCmd.exe /Action=AssessTargetReadiness
/AssessmentName="TestAssessment"
/SourceConnections="Server=SQLServerInstanceName;Integrated Security=true"
/AssessmentOverwriteResult
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"

```

**Évaluation de la disponibilité cible en important le rapport de découverte des fonctionnalités créé précédemment**

```
DmaCmd.exe /Action=AssessTargetReadiness
/AssessmentName="TestAssessment"
/ImportFeatureDiscoveryReportJson="c:\temp\feature_report.json" 
/AssessmentOverwriteResult
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"

```

**Évaluation de la disponibilité cible en fournissant un fichier de configuration**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/TargetReadinessConfiguration=.\Config.xml
```

Contenu du fichier de configuration lors de l’utilisation de connexions source :

```
<?xml version="1.0" encoding="utf-8" ?>
<TargetReadinessConfiguration xmlns="https://microsoft.com/schemas/SqlServer/Advisor/TargetReadinessConfiguration">
  <AssessmentName>name</AssessmentName>
  <SourcePlatform>Source Platform</SourcePlatform> <!-- Optional. The default is SqlOnPrem -->
  <TargetPlatform>TargetPlatform</TargetPlatform> <!-- Optional. The default is ManagedSqlServer -->
  <SourceConnections>
    <SourceConnection>connection string 1</SourceConnection>
    <SourceConnection>connection string 2</SourceConnection>
    <!-- ... -->
    <SourceConnection>connection string n</SourceConnection>
  </SourceConnections>
  <AssessmentResultJson>path\to\file.json</AssessmentResultJson>
  <FeatureDiscoveryReportJson>path\to\featurediscoveryreport.json</FeatureDiscoveryReportJson>
  <OverwriteResult>true</OverwriteResult> <!-- or false -->
</TargetReadinessConfiguration>
```

Contenu du fichier de configuration lors de l’importation du rapport de découverte des fonctionnalités :

```
<TargetReadinessConfiguration xmlns="https://microsoft.com/schemas/SqlServer/Advisor/TargetReadinessConfiguration">
  <AssessmentName>name</AssessmentName>
  <ImportFeatureDiscoveryReportJson>path\to\featurediscoveryfile.json</ImportFeatureDiscoveryReportJson>
  <AssessmentResultJson>path\to\resultfile.json</AssessmentResultJson>
  <OverwriteResult>true</OverwriteResult><!-- or false -->
</TargetReadinessConfiguration>
```

## <a name="azure-sql-databasemanaged-instance-sku-recommendations-using-the-cli"></a>Recommandations relatives aux références SKU d’instance gérée/Azure SQL Database à l’aide de l’interface CLI

Ces commandes prennent en charge des recommandations pour les deux Azure SQL Database options de déploiement de base de données unique et d’instance gérée.

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true 
```

|Argument  |Description  | Obligatoire (o/N)
|---------|---------|---------------|
|`/Action=SkuRecommendation` | Exécuter l’évaluation de la référence SKU à l’aide de la ligne de commande DMA | O
|`/SkuRecommendationInputDataFilePath` | Chemin d’accès complet au fichier de compteur de performances collecté à partir de l’ordinateur hébergeant vos bases de données | O
|`/SkuRecommendationTsvOutputResultsFilePath` | Chemin d’accès complet au fichier de résultats TSV | O <br> (Nécessite un chemin d’accès TSV ou JSON ou un fichier HTML)
|`/SkuRecommendationJsonOutputResultsFilePath` | Chemin d’accès complet au fichier de résultats JSON | O <br> (Nécessite un chemin d’accès TSV ou JSON ou un fichier HTML)
|`/SkuRecommendationHtmlResultsFilePath` | Chemin d’accès complet au fichier de résultats HTML | O <br> (Nécessite un chemin d’accès TSV ou JSON ou un fichier HTML)
|`/SkuRecommendationPreventPriceRefresh` | Empêche l’actualisation du prix. Utilisez si l’exécution est en mode hors connexion (par exemple, true). | O <br> (Sélectionnez cet argument pour les prix statiques, ou tous les arguments ci-dessous doivent être sélectionnés pour obtenir les prix les plus récents)
|`/SkuRecommendationCurrencyCode` | Devise dans laquelle afficher les prix (par exemple, « USD ») | O <br> (Pour les prix les plus récents)
|`/SkuRecommendationOfferName` | Nom de l’offre (par exemple, « MS-AZR-0003P »). Pour plus d’informations, consultez la page Détails de l' [offre Microsoft Azure](https://azure.microsoft.com/support/legal/offer-details/) . | O <br> (Pour les prix les plus récents)
|`/SkuRecommendationRegionName` | Nom de la région (par exemple, « Ouest ») | O <br> (Pour les prix les plus récents)
|`/SkuRecommendationSubscriptionId` | ID de l’abonnement. | O <br> (Pour les prix les plus récents)
|`/SkuRecommendationDatabasesToRecommend` | Liste des bases de données à recommander, séparées par des espaces (par exemple « Database1 », « Database2 » « Database3 »). Les noms respectent la casse et doivent être placés entre guillemets doubles. En cas d’omission, des recommandations sont fournies pour toutes les bases de données. | N
|`/AzureAuthenticationTenantId` | Locataire d’authentification. | O <br> (Pour les prix les plus récents)
|`/AzureAuthenticationClientId` | ID client de l’application AAD utilisée pour l’authentification. | O <br> (Pour les prix les plus récents)
|`/AzureAuthenticationInteractiveAuthentication` | Affectez la valeur true pour afficher la fenêtre. | O <br> (Pour les prix les plus récents) <br>(Choisissez l’une des 3 options d’authentification-option 1)
|`/AzureAuthenticationCertificateStoreLocation` | Définissez sur l’emplacement du magasin de certificats (par exemple, « CurrentUser »). | O <br>(Pour les prix les plus récents) <br> (Choisissez l’une des 3 options d’authentification-option 2)
|`/AzureAuthenticationCertificateThumbprint` | Définissez sur l’empreinte numérique du certificat. | O <br> (Pour les prix les plus récents) <br>(Choisissez l’une des 3 options d’authentification-option 2)
|`/AzureAuthenticationToken` | Définissez sur le jeton de certificat. | O <br> (Pour les prix les plus récents) <br>(Choisissez l’une des 3 options d’authentification-option 3)

## <a name="examples-of-sku-assessments-using-the-cli"></a>Exemples d’évaluations de références SKU à l’aide de l’interface CLI

**Dmacmd. exe**

`Dmacmd.exe /? or DmaCmd.exe /help`

**Recommandation de la référence SKU d’Azure SQL DB/MI avec actualisation du prix (Obtient les prix les plus récents)-authentification interactive** 

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
/AzureAuthenticationInteractiveAuthentication=true 
```

**Recommandation de la référence SKU d’Azure SQL DB/MI avec actualisation du prix (récupération des derniers prix)-authentification par certificat**

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
/AzureAuthenticationCertificateStoreLocation=<Your Certificate Store Location>
/AzureAuthenticationCertificateThumbprint=<Your Certificate Thumbprint>  
```

**Recommandation de référence SKU/MI d’Azure SQL DB avec actualisation des prix (récupération des derniers prix)-authentification par jeton et spécification des bases de données à recommander**
  
```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationCurrencyCode=USD
/SkuRecommendationOfferName=MS-AZR-0044p
/SkuRecommendationRegionName=UKWest
/SkuRecommendationDatabasesToRecommend=“TPCDS1G,EDW_3G,TPCDS10G”
/SkuRecommendationSubscriptionId=<Your Subscription Id>
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
/AzureAuthenticationToken=<Your Authentication Token> 
```

**Recommandation de référence SKU Azure SQL DB/MI sans actualisation du prix (utiliser des prix statiques)** 
```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true  
```

## <a name="see-also"></a>Voir aussi
- [Assistant Migration de données](https://aka.ms/get-dma) Télécharger.
- L’article [identifie la référence SKU Azure SQL Database appropriée pour votre base de données locale](https://aka.ms/dma-sku-recommend-sqldb).
