---
title: Exécutez l’Assistant Migration des données à partir de la ligne de commande (SQL Server) | Microsoft Docs
description: Découvrez comment exécuter l’Assistant Migration des données à partir de la ligne de commande pour évaluer les bases de données SQL Server pour la migration
ms.custom: ''
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
manager: jroth
ms.openlocfilehash: 18ac429a536b657b7f7c0cf91c100eed8a152e52
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794401"
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>Exécutez l’Assistant Migration des données à partir de la ligne de commande

Avec la version 2.1 et versions ultérieures, lorsque vous installez Data Migration Assistant, il installe également dmacmd.exe dans *% ProgramFiles%\\Microsoft Data Migration Assistant\\* . Utilisez dmacmd.exe pour évaluer vos bases de données en mode sans assistance et renvoyer le résultat au fichier JSON ou CSV. Cette méthode est particulièrement utile lors de l’évaluation de plusieurs bases de données ou des bases de données énormes. 

> [!NOTE]
> Dmacmd.exe prend en charge uniquement les évaluations en cours d’exécution. Migrations ne sont pas prises en charge pour l’instant.

## <a name="assessments-using-the-command-line-interface-cli"></a>Évaluations à l’aide de l’Interface de ligne de commande (CLI)

```
DmaCmd.exe /AssessmentName="string"
/AssessmentDatabases="connectionString1" \["connectionString2"\]
\[/AssessmentSourcePlatform="SourcePlatform"]
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
|`/AssessmentSourcePlatform`     | Plateforme de la source pour l’évaluation : <br>Valeurs prises en charge pour l’évaluation : SqlOnPrem, RdsSqlServer (valeur par défaut) <br>Valeurs prises en charge pour l’évaluation de la disponibilité cible : SqlOnPrem, RdsSqlServer (valeur par défaut), Cassandra (version préliminaire)   | N
|`/AssessmentTargetPlatform`     | Plateforme cible pour l’évaluation :  <br> Valeurs prises en charge pour l’évaluation : AzureSqlDatabase, ManagedSqlServer, SqlServer2012, SqlServer2014, SqlServer2016, SqlServerLinux2017 et SqlServerWindows2017 (valeur par défaut)  <br> Valeurs prises en charge pour l’évaluation de la disponibilité cible : ManagedSqlServer (valeur par défaut), CosmosDB (version préliminaire)   | N
|`/AssessmentEvaluateFeatureParity`  | Exécuter des règles de parité de fonctionnalité. Si la plateforme de la source est RdsSqlServer, évaluation de parité de fonctionnalité n’est pas pris en charge pour la plateforme cible AzureSqlDatabase  | N
|`/AssessmentEvaluateCompatibilityIssues`     | Exécuter les règles de compatibilité  | O <br> (AssessmentEvaluateCompatibilityIssues ou AssessmentEvaluateRecommendations est requises.)
|`/AssessmentEvaluateRecommendations`     | Exécuter les recommandations de fonctionnalité        | O <br> (AssessmentEvaluateCompatibilityIssues ou AssessmentEvaluateRecommendations est requises)
|`/AssessmentOverwriteResult`     | Remplacer le fichier de résultat    | N
|`/AssessmentResultJson`     | Chemin d’accès complet au fichier de résultat JSON     | O <br> (AssessmentResultJson ou AssessmentResultCsv est requis)
|`/AssessmentResultCsv`    | Chemin d’accès complet au fichier CSV   | O <br> (AssessmentResultJson ou AssessmentResultCsv est requis)
|`/Action`    | Utilisez SkuRecommendation pour obtenir des recommandations de référence (SKU), AssessTargetReadiness permet d’effectuer l’évaluation de la disponibilité cible.   | N
|`/SourceConnections`    | Liste délimitée par des espaces des chaînes de connexion. Nom de la base de données (catalogue Initial) est facultatif. Si aucun nom de base de données est fourni, toutes les bases de données sur la source sont évaluées.   | O <br> (Obligatoire si Action est « AssessTargetReadiness »)
|`/TargetReadinessConfiguration`    | Chemin d’accès complet au fichier XML décrivant les valeurs de nom, les connexions à la source et le fichier de résultats.   | O <br> (TargetReadinessConfiguration ou SourceConnections est requises)
|`/FeatureDiscoveryReportJson`    | Chemin d’accès à la découverte de la fonctionnalité rapports JSON. Si ce fichier est généré, il peut être utilisé pour réexécuter l’évaluation de la disponibilité cible sans vous connecter à la source. | N
|`/ImportFeatureDiscoveryReportJson`    | Chemin d’accès au rapport JSON de détection de fonctionnalité créé précédemment. Au lieu de connexions de source, ce fichier sera utilisé.   | N

## <a name="examples-of-assessments-using-the-cli"></a>Exemples d’évaluations à l’aide de l’interface CLI

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Évaluation de bases de données unique à l’aide de règles de compatibilité de l’authentification et en cours d’exécution Windows**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentEvaluateCompatibilityIssues /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
```

**Évaluation de la base de données unique à l’aide de la recommandation de fonctionnalité d’authentification et en cours d’exécution de SQL Server**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;User Id=myUsername;Password=myPassword;"
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
```

**Évaluation de base de données unique pour la plateforme cible SQL Server 2012, enregistrer les résultats dans le fichier .json et .csv**

```
DmaCmd.exe /AssessmentName="TestAssessment"
/AssessmentDatabases="Server=SQLServerInstanceName;Initial
Catalog=DatabaseName;Integrated Security=true"
/AssessmentTargetPlatform="SqlServer2012"
/AssessmentEvaluateRecommendations /AssessmentOverwriteResult
/AssessmentResultJson="C:\\temp\\Results\\AssessmentReport.json"
/AssessmentResultCsv="C:\\temp\\Results\\AssessmentReport.csv"
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

**Évaluation de la disponibilité de cible unique-base de données à l’aide de l’authentification Windows**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/SourceConnections="Server=SQLServerInstanceName;Initial Catalog=DatabaseName;Integrated Security=true" 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"
```

**Évaluation de la disponibilité de cible unique-base de données à l’aide de l’authentification SQL Server**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/AssessmentName="TestAssessment" 
/SourceConnections="Server=SQLServerInstanceName;Initial Catalog=DatabaseName;User Id=myUsername;Password=myPassword;" /AssessmentEvaluateRecommendations 
/AssessmentOverwriteResult 
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json" 

```

**Évaluation de la base de données unique pour la plateforme cible de base de données SQL Azure, enregistrez les résultats dans un fichier .json et .csv**

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

**Plusieurs bases de données cible Readiness assessment**

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

**Cible Readiness assessment pour toutes les bases de données sur un serveur à l’aide de l’authentification Windows**

```
DmaCmd.exe /Action=AssessTargetReadiness
/AssessmentName="TestAssessment"
/SourceConnections="Server=SQLServerInstanceName;Integrated Security=true"
/AssessmentOverwriteResult
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"

```

**Évaluation de la disponibilité cible en important des rapports de détection de fonctionnalité créé précédemment**

```
DmaCmd.exe /Action=AssessTargetReadiness
/AssessmentName="TestAssessment"
/ImportFeatureDiscoveryReportJson="c:\temp\feature_report.json" 
/AssessmentOverwriteResult
/AssessmentResultJson="C:\temp\Results\AssessmentReport.json"

```

**Évaluation de la disponibilité cible en fournissant le fichier de configuration**

```
DmaCmd.exe /Action=AssessTargetReadiness 
/TargetReadinessConfiguration=.\Config.xml
```

Connexions de source de contenu du fichier de configuration lorsque vous utilisez :

```
<?xml version="1.0" encoding="utf-8" ?>
<TargetReadinessConfiguration xmlns="http://microsoft.com/schemas/SqlServer/Advisor/TargetReadinessConfiguration">
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

Contenu du fichier de configuration lors de l’importation du composant rapport de découverte :

```
<TargetReadinessConfiguration xmlns="http://microsoft.com/schemas/SqlServer/Advisor/TargetReadinessConfiguration">
  <AssessmentName>name</AssessmentName>
  <ImportFeatureDiscoveryReportJson>path\to\featurediscoveryfile.json</ImportFeatureDiscoveryReportJson>
  <AssessmentResultJson>path\to\resultfile.json</AssessmentResultJson>
  <OverwriteResult>true</OverwriteResult><!-- or false -->
</TargetReadinessConfiguration>
```

## <a name="azure-sql-databasemanaged-instance-sku-recommendations-using-the-cli"></a>Azure SQL Database/managed instance recommandations de référence (SKU) à l’aide de l’interface CLI

Ces commandes prennent en charge les recommandations pour la base de données Azure SQL Database unique et options de déploiement d’instance gérée.

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true 
```

|Argument  |Description  | Requis (Y/N)
|---------|---------|---------------|
|`/Action=SkuRecommendation` | Exécuter l’évaluation de référence (SKU) à l’aide de la ligne de commande DMA | O
|`/SkuRecommendationInputDataFilePath` | Chemin d’accès complet au fichier de compteur de performances collectées à partir de l’ordinateur qui héberge vos bases de données | O
|`/SkuRecommendationTsvOutputResultsFilePath` | Chemin d’accès complet au fichier TSV | O <br> (Nécessite le chemin d’accès de fichier TSV ou JSON ou HTML)
|`/SkuRecommendationJsonOutputResultsFilePath` | Chemin d’accès complet au fichier de résultat JSON | O <br> (Nécessite le chemin d’accès de fichier TSV ou JSON ou HTML)
|`/SkuRecommendationHtmlResultsFilePath` | Chemin d’accès complet au fichier HTML | O <br> (Nécessite le chemin d’accès de fichier TSV ou JSON ou HTML)
|`/SkuRecommendationPreventPriceRefresh` | Empêche l’actualisation de prix. Utilisez si en cours d’exécution en mode hors connexion (par exemple, true). | O <br> (Sélectionnez soit cet argument pour connaître les prix statiques ou tous les arguments ci-dessous doivent être sélectionnés pour obtenir les derniers cours)
|`/SkuRecommendationCurrencyCode` | La devise dans laquelle afficher les prix (par exemple) « USD ») | O <br> (Pour connaître les prix)
|`/SkuRecommendationOfferName` | Nom de l’offre (par exemple) "MS-AZR-0003P"). Pour plus d’informations, consultez le [détails de l’offre Microsoft Azure](https://azure.microsoft.com/support/legal/offer-details/) page. | O <br> (Pour connaître les prix)
|`/SkuRecommendationRegionName` | Nom de la région (par exemple) « WestUS ») | O <br> (Pour connaître les prix)
|`/SkuRecommendationSubscriptionId` | L'ID de l'abonnement. | O <br> (Pour connaître les prix)
|`/SkuRecommendationDatabasesToRecommend` | Liste séparée par espace des bases de données pour recommander (par exemple, pour « Database1 » « Database2 » « Database3 »). Noms respectent la casse et doivent être entourées de guillemets doubles. Si omis, les recommandations sont fournies pour toutes les bases de données. | N
|`/AzureAuthenticationTenantId` | Le client d’authentification. | O <br> (Pour connaître les prix)
|`/AzureAuthenticationClientId` | L’ID client de l’application AAD utilisée pour l’authentification. | O <br> (Pour connaître les prix)
|`/AzureAuthenticationInteractiveAuthentication` | La valeur true pour afficher la fenêtre. | O <br> (Pour connaître les prix) <br>(Choisissez une des options de 3 authentification - option 1)
|`/AzureAuthenticationCertificateStoreLocation` | (Par exemple, la valeur est l’emplacement du magasin de certificats « CurrentUser »). | O <br>(Pour connaître les prix) <br> (Choisissez une des options de 3 authentification - option 2)
|`/AzureAuthenticationCertificateThumbprint` | La valeur est l’empreinte numérique du certificat. | O <br> (Pour connaître les prix) <br>(Choisissez une des options de 3 authentification - option 2)
|`/AzureAuthenticationToken` | Définir sur le jeton de certificat. | O <br> (Pour connaître les prix) <br>(Choisissez une des options de 3 authentification - option 3)

## <a name="examples-of-sku-assessments-using-the-cli"></a>Exemples d’évaluations de référence (SKU) à l’aide de l’interface CLI

**Dmacmd.exe**

`Dmacmd.exe /? or DmaCmd.exe /help`

**Recommandation d’Azure SQL DB/MI SKU avec actualisation price (prix dernière get) - authentification Interactive** 

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

**Recommandation d’Azure SQL DB/MI SKU avec actualisation price (prix dernière get) - l’authentification par certificat**

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

**Recommandation d’Azure SQL DB référence (SKU) / MI avec actualisation price (prix plus récente de get -), l’authentification des jetons et spécifier les bases de données pour recommander des**
  
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

**Recommandation d’Azure SQL DB/MI SKU sans actualisation price (prix statique d’utilisation)** 
```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true  
```

## <a name="see-also"></a>Voir aussi
- [Assistant Migration des données](https://aka.ms/get-dma) télécharger.
- L’article [identifier la référence SKU à base de données SQL Azure appropriée pour votre base de données locale](https://aka.ms/dma-sku-recommend-sqldb).
