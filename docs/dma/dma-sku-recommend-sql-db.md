---
title: Identifier la référence SKU à base de données SQL Azure appropriée pour votre base de données locale (Data Migration Assistant) | Microsoft Docs
description: Découvrez comment utiliser l’Assistant de Migration de données pour identifier le droit SKU de base de données SQL Azure pour votre base de données locale
ms.custom: ''
ms.date: 08/29/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: rajpo
manager: craigg
ms.openlocfilehash: 84601b6a556df64d3708fd749af06be8e753048d
ms.sourcegitcommit: 010755e6719d0cb89acb34d03c9511c608dd6c36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43240147"
---
# <a name="identify-the-right-azure-sql-database-sku-for-your-on-premises-database"></a>Identifier la référence SKU à base de données SQL Azure appropriée pour votre base de données locale

La tâche de migration de vos bases de données vers le cloud est un complexe et fastidieuse, impliquant un nombre de variables. Sélection de la cible de la base de données Azure correct et de la référence (SKU) pour votre base de données peut s’avérer difficile. Notre objectif avec la base de données de Migration Assistant (DMA) est pour résoudre ces problèmes et pour améliorer votre migration de base de données expérience simple et efficace.

Cet article se concentre essentiellement sur la fonctionnalité de recommandations de SKU de base de données SQL Azure de DMA, qui vous permet d’identifier le minimum recommandé SKU de base de données SQL Azure en fonction des compteurs de performances collectés à partir des ou les ordinateurs hébergeant vos bases de données. Cette fonctionnalité fournit des recommandations relatives à la tarification du niveau, de niveau de calcul et de taille maximale de données, ainsi que coût estimé par mois. Il offre également la possibilité de configurer toutes vos bases de données vers Azure en bloc.

> [!NOTE] 
> Cette fonctionnalité est actuellement disponible uniquement via l’Interface de ligne de commande (CLI). Prise en charge de cette fonctionnalité via l’interface utilisateur DMA figurera dans une prochaine version.

> [!IMPORTANT]
> Recommandations de référence (SKU) pour Azure SQL Database sont actuellement disponibles pour les migrations à partir de SQL Server 2016 ou version ultérieure.

Les instructions suivantes vous permettent de déterminer les recommandations de référence de base de données SQL Azure et configurer les bases de données associées vers Azure, à l’aide de Data Migration Assistant.

## <a name="prerequisites"></a>Prérequis

Télécharger l’Assistant de Migration de base de données version 4.0 ou version ultérieure, puis installez-le. Si vous avez déjà l’outil installé, fermez et rouvrez, et vous êtes invité à mettre à niveau de l’outil.

## <a name="collect-performance-counters"></a>Collecter les compteurs de performances

La première étape du processus consiste à collecter les compteurs de performances de vos bases de données. Vous pouvez collecter les compteurs de performances en exécutant une commande PowerShell sur l’ordinateur qui héberge vos bases de données. DMA vous fournit une copie de ce fichier de PowerShell, mais vous pouvez également utiliser votre propre méthode pour capturer les compteurs de performances de votre ordinateur.

Vous n’avez pas besoin effectuer cette tâche pour chaque base de données individuellement. Les compteurs de performances collectées à partir d’un ordinateur peuvent être utilisés pour recommander la référence (SKU) pour toutes les bases de données hébergées sur l’ordinateur.

> [!IMPORTANT]
> L’ordinateur à partir duquel vous exécutez cette commande requiert des autorisations d’administrateur sur l’ordinateur qui héberge vos bases de données.

1. Vérifiez que le fichier de PowerShell nécessaire pour collecter les compteurs de performances est installé dans le dossier DMA.

    ![Fichier PowerShell indiqué dans le dossier DMA](../dma/media/dma-sku-recommend-data-collection-file.png)

2. Exécutez le script PowerShell avec les arguments suivants :
    - **ComputerName**: le nom de l’ordinateur qui héberge vos bases de données.
    - **OutputFilePath**: le chemin d’accès du fichier de sortie pour enregistrer les compteurs collectés.
    - **CollectionTimeInSeconds**: la durée pendant laquelle vous souhaitez collecter des données de compteur de performances.
      Capturer les compteurs de performance pour au moins 40 minutes obtenir une recommandation éloquent. Plus la durée de la capture, plus précises la recommandation sera.
    - **DbConnectionString**: chaîne de la connexion qui pointe vers la base de données principale hébergée sur l’ordinateur à partir de laquelle vous collectez des données de compteur de performances.
     
    Voici un exemple d’appel :

    ```
    .\SkuRecommendationDataCollectionScript.ps1
     -ComputerName Foobar1
     -OutputFilePath D:\counters2.csv
     -CollectionTimeInSeconds 10
     -DbConnectionString "Server=localhost;Initial Catalog=master;Integrated Security=SSPI;"
    ```
    
    Une fois la commande exécutée, le processus génère un fichier avec les compteurs de performances dans l’emplacement spécifié. Ce fichier peut être utilisé en tant qu’entrée pour la commande de recommandation de référence (SKU) dans la section suivante.

## <a name="use-the-dma-cli-to-get-sku-recommendations"></a>Utiliser CLI DMA pour obtenir des recommandations de référence (SKU)

Utiliser le fichier de sortie des compteurs de performances à partir de l’étape précédente comme entrée pour cette étape. DMA vous fournira les recommandations pour la base de données SQL Azure niveau tarifaire, le niveau de calcul et la taille maximale des données pour chaque base de données sur votre ordinateur. DMA également vous fournira le coût mensuel estimé pour chaque base de données.

Exécutez le dmacmd.exe avec les arguments suivants :

- **/ Action = SkuRecommendation**: entrez cet argument pour exécuter des évaluations de la référence (SKU).
- **/ SkuRecommendationInputDataFilePath**: le chemin d’accès au fichier de compteur collectées dans la section précédente.
- **/ SkuRecommendationTsvOutputResultsFilePath**: le chemin d’accès pour écrire les résultats de sortie au format TSV.
- **/ SkuRecommendationJsonOutputResultsFilePath**: le chemin d’accès pour écrire les résultats de sortie au format JSON.
- **/ SkuRecommendationHtmlResultsFilePath**: chemin d’accès pour écrire les résultats de sortie au format HTML.

En outre, vous devez choisir l’un des arguments suivants :
- Empêcher l’actualisation de prix
    - **/ SkuRecommendationPreventPriceRefresh**: empêche l’actualisation de prix. Utilisez si en cours d’exécution en mode hors connexion.
- Obtenir les derniers cours 
    - **/ SkuRecommendationCurrencyCode**: la devise dans laquelle afficher les prix (par exemple) « USD »).
    - **/ SkuRecommendationOfferName**: nom de l’offre (par exemple) « MS-AZR - 0003P »). Pour plus d’informations, consultez le [détails de l’offre Microsoft Azure](https://azure.microsoft.com/support/legal/offer-details/) page.
    - **/ SkuRecommendationRegionName**: nom de la région (par exemple) « WestUS »).
    - **/ SkuRecommendationSubscriptionId**: l’ID d’abonnement.
    - **/ AzureAuthenticationTenantId**: le client d’authentification.
    - **/ AzureAuthenticationClientId**: l’ID client de l’application AAD utilisée pour l’authentification.
    - L’une des options d’authentification suivantes :
        - Interactif
            - **AzureAuthenticationInteractiveAuthentication**: la valeur true pour une fenêtre contextuelle d’authentification.
        - Basée sur les certificats
            - **AzureAuthenticationCertificateStoreLocation**: (par exemple, la valeur est l’emplacement du magasin de certificats « CurrentUser »).
            - **AzureAuthenticationCertificateThumbprint**: la valeur est l’empreinte numérique du certificat.
        - Jeton basé
            - **AzureAuthenticationToken**: la valeur est le jeton de certificat.

Voici certains appels de l’exemple :

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

Le fichier de sortie TSV contiendra les colonnes affichées dans le graphique suivant :

   ![Fichier PowerShell indiqué dans le dossier DMA](../dma/media/dma-tsv-file-column.png)

Une description de chaque colonne suit.

- **DatabaseName** – le nom de votre base de données.
- **MetricName** : si une mesure a été exécutée ou non.
- **MetricType** -niveau de base de données SQL Azure recommandé.
- **MetricValue** -recommandé de base de données SQL Azure référence (SKU).
- **SQLMiEquivalentCores** -si vous souhaitez aller pour Azure SQL Database Managed Instance, vous pouvez utiliser cette valeur pour le nombre de cœurs.
- **IsTierRecommended** -nous nous assurons une recommandation de référence (SKU) minimale pour chaque niveau. Nous appliquons ensuite les paramètres heuristiques pour déterminer le niveau approprié pour votre base de données. 
- **ExclusionReasons** -cette valeur est vide si un niveau est recommandé. Pour chaque niveau qui n’est pas recommandé, nous fournissons les raisons pourquoi il n’était pas récupéré.
- **AppliedRules** -une notation courte des règles qui ont été appliquées.

La valeur recommandée est la référence (SKU) minimale nécessaire pour vos requêtes à exécuter dans Azure avec un taux de réussite semblable à vos bases de données sur site. Par exemple, si la référence (SKU) minimale recommandée est S4 pour le niveau standard, puis en choisissant S3 ci-dessous sera provoquer l’expiration du délai des requêtes ou ne parviennent pas à exécuter.

Le fichier HTML contient ces informations dans un format graphique. Vous pouvez utiliser le fichier HTML à l’entrée des informations d’abonnement Azure, choisissez le niveau tarifaire, niveau et la taille maximale des données de calcul pour vos bases de données et générer un script pour configurer vos bases de données. Ce script peut être exécuté à l’aide de PowerShell.

## <a name="provision-your-databases-to-azure"></a>Configurer vos bases de données vers Azure
Avec seulement quelques clics, vous pouvez utiliser les recommandations de l’étape précédente pour les bases de données cibles approvisionner dans Azure à laquelle vous pouvez migrer vos bases de données. Vous pouvez également modifier les recommandations en mettant à jour le fichier HTML comme suit.

1. Ouvrez le fichier HTML et entrez les informations suivantes :
    - **ID d’abonnement** : l’ID d’abonnement de l’abonnement Azure auquel vous souhaitez approvisionner les bases de données.
    - **Région** – la région dans laquelle configurer les bases de données. Assurez-vous que votre abonnement prend en charge de la zone de sélection.
    - **Groupe de ressources** – le groupe de ressources auquel vous souhaitez déployer les bases de données. Entrez un groupe de ressources existant.
    - **Nom du serveur** – serveur de la base de données Azure SQL auquel vous souhaitez que les bases de données déployées. Si vous entrez un nom de serveur qui n’existe pas, il sera créé.
    - **Administrateur Username\Password** – le nom d’utilisateur administrateur de serveur et le mot de passe.

2. Passez en revue les recommandations pour chaque base de données et modifier le niveau tarifaire, niveau et la taille de données max en fonction des besoins de calcul. Veillez à désélectionner les bases de données que vous ne souhaitez pas actuellement à approvisionner.

3. Sélectionnez **générer un Script d’approvisionnement**, enregistrez le script, puis l’exécuter dans PowerShell.

    Ce processus doit créer les bases de données que vous avez sélectionné dans la page HTML.

Vous pouvez effectuer toutes les étapes de ce processus sur un seul ordinateur ou vous pouvez les exécuter sur plusieurs ordinateurs afin de déterminer les recommandations de référence (SKU) à grande échelle. DMA rend une expérience simple et évolutive en prenant en charge toutes ces étapes via l’Interface de ligne de commande. Là encore, la prise en charge pour cette fonctionnalité via l’interface utilisateur DMA sera disponible plus tard cette année.

## <a name="next-steps"></a>Étapes suivantes
- Téléchargez la dernière version de [Data Migration Assistant](https://aka.ms/get-dma).
- Consultez l’article [exécuter Data Migration Assistant à partir de la ligne de commande](https://docs.microsoft.com/sql/dma/dma-commandline?view=sql-server-2017) pour une liste complète des commandes utilisées pour exécuter le DMA à partir de l’interface CLI.
