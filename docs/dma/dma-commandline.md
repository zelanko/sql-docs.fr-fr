---
title: Exécutez l’Assistant Migration des données à partir de la ligne de commande (SQL Server) | Microsoft Docs
description: Découvrez comment exécuter l’Assistant Migration des données à partir de la ligne de commande pour évaluer les bases de données SQL Server pour la migration
ms.custom: ''
ms.date: 10/20/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Command Line
ms.assetid: ''
author: pochiraju
ms.author: rajpo
manager: craigg
ms.openlocfilehash: c308dc9e0f05ec8abed83a75a3a1d0ea396fd46c
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49643987"
---
# <a name="run-data-migration-assistant-from-the-command-line"></a>Exécutez l’Assistant Migration des données à partir de la ligne de commande
Avec la version 2.1 et versions ultérieures, lorsque vous installez Data Migration Assistant, il installe également dmacmd.exe dans *% ProgramFiles%\\Microsoft Data Migration Assistant\\*. Utilisez dmacmd.exe pour évaluer vos bases de données en mode sans assistance et renvoyer le résultat au fichier JSON ou CSV. Cette méthode est particulièrement utile lors de l’évaluation de plusieurs bases de données ou des bases de données énormes. 

> [!NOTE]
> Dmacmd.exe prend en charge uniquement les évaluations en cours d’exécution. Migrations ne sont pas prises en charge pour l’instant.


## <a name="assessments-using-the-command-line-interface-cli"></a>Évaluations à l’aide de l’Interface de ligne de commande (CLI)

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


## <a name="examples-of-assessments-using-the-cli"></a>Exemples d’évaluations à l’aide de l’interface CLI

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

## <a name="azure-sql-database-sku-recommendations-using-the-cli"></a>Recommandations de référence SKU de base de données SQL Azure à l’aide de l’interface CLI

> [!IMPORTANT]
> Recommandations de référence (SKU) pour Azure SQL Database sont actuellement disponibles pour les migrations à partir de SQL Server 2016 ou version ultérieure.

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
/AzureAuthenticationInteractiveAuthentication=true
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId>
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
```

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
|`/SkuRecommendationInputDataFilePath`  | Chemin d’accès complet au fichier de compteur de performances collectées à partir de l’ordinateur qui héberge vos bases de données |    O
|`/SkuRecommendationTsvOutputResultsFilePath`   | Chemin d’accès complet au fichier TSV |    O <br>(Le chemin d’accès de fichier TSV ou JSON ou HTML est requis)
|`/SkuRecommendationJsonOutputResultsFilePath`  | Chemin d’accès complet au fichier de résultat JSON |   O <br>(Le chemin d’accès de fichier TSV ou JSON ou HTML est requis)
|`/SkuRecommendationHtmlResultsFilePath` |  Chemin d’accès complet au fichier HTML | O <br>(Le chemin d’accès de fichier TSV ou JSON ou HTML est requis)
|`/SkuRecommendationPreventPriceRefresh` |  Empêche l’actualisation de prix. Utilisez si en cours d’exécution en mode hors connexion. |    O <br>(Cet argument est sélectionné pour connaître les prix statiques ou tous les arguments ci-dessous doivent être sélectionnés pour l’obtention des prix les plus récents)
|`/SkuRecommendationCurrencyCode` | La devise dans laquelle afficher les prix (par exemple) « USD ») | O <br>(Si vous souhaitez obtenir les derniers cours)
|`/SkuRecommendationOfferName` |    Nom de l’offre (par exemple) « MS-AZR - 0003P »). Pour plus d’informations, consultez le [détails de l’offre Microsoft Azure](https://azure.microsoft.com/support/legal/offer-details/) page. |   O <br>(Si vous souhaitez obtenir les derniers cours)
|`/SkuRecommendationRegionName` |   Nom de la région (par exemple) « WestUS ») |   O <br>(Si vous souhaitez obtenir les derniers cours)
|`/SkuRecommendationSubscriptionId` | L'ID de l'abonnement. |    O <br>(Si vous souhaitez obtenir les derniers cours)
|`/AzureAuthenticationTenantId` | Le client d’authentification. |  O <br>(Si vous souhaitez obtenir les derniers cours)
|`/AzureAuthenticationClientId` | L’ID client de l’application AAD utilisée pour l’authentification. | O <br>(Si vous souhaitez obtenir les derniers cours)
|`/AzureAuthenticationInteractiveAuthentication`    | La valeur true pour afficher la fenêtre. |   O <br>(Si vous souhaitez obtenir les derniers cours) <br>(Choisissez une des options de 3 authentification - option 1)
|`/AzureAuthenticationCertificateStoreLocation` | (Par exemple, la valeur est l’emplacement du magasin de certificats « CurrentUser »). | O <br>(Si vous souhaitez obtenir les derniers cours) <br>(Choisissez une des options de 3 authentification - option 2)
|`/AzureAuthenticationCertificateThumbprint`    | La valeur est l’empreinte numérique du certificat. | O <br>(Si vous souhaitez obtenir les derniers cours) <br>(Choisissez une des options de 3 authentification - option 2)
|`/AzureAuthenticationToken` |  Définir sur le jeton de certificat. | O <br>(Si vous souhaitez obtenir les derniers cours) <br>(Choisissez une des options de 3 authentification - option 3)

## <a name="examples-of-sku-assessments-using-the-cli"></a>Exemples d’évaluations de référence (SKU) à l’aide de l’interface CLI

**Dmacmd.exe**

  `Dmacmd.exe /? or DmaCmd.exe /help`

**Recommandation de référence SKU de base de données SQL Azure avec l’actualisation price (prix plus récente de get -) d’authentification Interactive** 
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

**Recommandation de référence SKU de base de données SQL Azure avec l’actualisation price (prix plus récente de get -) l’authentification par certificat**
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

**Jeton de la recommandation de référence SKU de base de données SQL Azure avec l’actualisation price (prix plus récente de get -) authentification**  
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
/AzureAuthenticationToken=<Your Authentication Token> 
```

**Recommandation de référence SKU de base de données SQL Azure sans actualisation price (prix statique d’utilisation)** 
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
