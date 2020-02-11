---
title: Identifiez la référence SKU Azure SQL Database appropriée pour votre base de données locale (Assistant Migration de données) | Microsoft Docs
description: Découvrez comment utiliser Assistant Migration de données pour identifier la référence SKU Azure SQL Database adaptée à votre base de données locale.
ms.custom: ''
ms.date: 05/06/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: jtoland
ms.openlocfilehash: d6d329b97946d9d8042641653ed0167510a19b17
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "72586738"
---
# <a name="identify-the-right-azure-sql-databasemanaged-instance-sku-for-your-on-premises-database"></a>Identifier la référence SKU Azure SQL Database/Managed Instance appropriée pour votre base de données locale

La migration des bases de données vers le Cloud peut être compliquée, en particulier lors de la tentative de sélection de la meilleure cible de base de données Azure et de la référence SKU de votre base de données. L’objectif de la Assistant Migration de base de données (DMA) est de vous aider à répondre à ces questions et à faciliter la migration de votre base de données en fournissant ces recommandations SKU dans une sortie conviviale.

Cet article se concentre sur la fonctionnalité de recommandation Azure SQL Database SKU de DMA. Azure SQL Database propose plusieurs options de déploiement, notamment :

- Base de données unique
- Pools élastiques
- Instance gérée

La fonctionnalité recommandations SKU vous permet d’identifier la référence minimale recommandée Azure SQL Database base de données unique ou d’instance gérée en fonction des compteurs de performances collectés sur le ou les ordinateurs hébergeant vos bases de données. Cette fonctionnalité fournit des recommandations relatives au niveau tarifaire, au niveau de calcul et à la taille maximale des données, ainsi qu’au coût estimé par mois. Il offre également la possibilité d’approvisionner en bloc des bases de données uniques et des instances gérées dans Azure pour toutes les bases de données recommandées.

> [!NOTE]
> Cette fonctionnalité n’est actuellement disponible qu’à l’aide de l’interface de ligne de commande (CLI).

Voici des instructions pour vous aider à déterminer les recommandations de Azure SQL Database SKU et à approvisionner une ou plusieurs bases de données uniques dans Azure à l’aide de DMA.

## <a name="prerequisites"></a>Conditions préalables requises

- Téléchargez et installez la dernière version de [DMA](https://aka.ms/get-dma). Si vous disposez déjà d’une version antérieure de l’outil, ouvrez-la et vous serez invité à mettre à niveau DMA.
- Assurez-vous que votre ordinateur dispose de [PowerShell Version 5,1](https://www.microsoft.com/download/details.aspx?id=54616) ou ultérieure, ce qui est nécessaire pour exécuter tous les scripts. Pour plus d’informations sur la findoug de la version de PowerShell installée sur votre ordinateur, consultez l’article [Télécharger et installer Windows PowerShell 5,1](https://docs.microsoft.com/skypeforbusiness/set-up-your-computer-for-windows-powershell/download-and-install-windows-powershell-5-1).
- Assurez-vous que le module Azure PowerShell est installé sur votre ordinateur. Pour plus d’informations, consultez l’article [installer le module Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-1.8.0).
- Vérifiez que le fichier PowerShell **SkuRecommendationDataCollectionScript. ps1**, qui est requis pour collecter les compteurs de performances, est installé dans le dossier DMA.
- Assurez-vous que l’ordinateur sur lequel vous allez effectuer ce processus dispose des autorisations d’administrateur sur l’ordinateur qui héberge vos bases de données.

## <a name="collect-performance-counters"></a>Collecter les compteurs de performances

La première étape du processus consiste à collecter les compteurs de performances de vos bases de données. Vous pouvez collecter des compteurs de performances en exécutant une commande PowerShell sur l’ordinateur hébergeant vos bases de données. DMA vous fournit une copie de ce fichier PowerShell, mais vous pouvez également utiliser votre propre méthode pour capturer des compteurs de performances à partir de votre ordinateur.

Vous n’avez pas besoin d’effectuer cette tâche pour chaque base de données individuellement. Les compteurs de performance collectés à partir d’un ordinateur peuvent être utilisés pour recommander la référence SKU pour toutes les bases de données hébergées sur l’ordinateur.

1. Dans le dossier DMA, localisez le fichier PowerShell SkuRecommendationDataCollectionScript. ps1. Ce fichier est nécessaire pour collecter les compteurs de performances.

    ![Fichier PowerShell affiché dans le dossier DMA](../dma/media/dma-sku-recommend-data-collection-file.png)

2. Exécutez le script PowerShell avec les arguments suivants :
    - **ComputerName**: nom de l’ordinateur qui héberge vos bases de données.
    - **OutputFilePath**: chemin d’accès au fichier de sortie pour enregistrer les compteurs collectés.
    - **CollectionTimeInSeconds**: durée pendant laquelle vous souhaitez collecter les données des compteurs de performances. Capturez les compteurs de performances pendant au moins 40 minutes pour obtenir une recommandation explicite. Plus la durée de la capture est longue, plus la recommandation sera précise. Assurez-vous également que les charges de travail sont en cours d’exécution pour les bases de données souhaitées, afin d’obtenir des recommandations plus précises.
    - **DbConnectionString**: chaîne de connexion pointant vers la base de données Master hébergée sur l’ordinateur à partir duquel vous collectez les données des compteurs de performances.

    Voici un exemple d’appel :

    ```
    .\SkuRecommendationDataCollectionScript.ps1
     -ComputerName Foobar1
     -OutputFilePath D:\counters2.csv
     -CollectionTimeInSeconds 2400
     -DbConnectionString "Server=localhost;Initial Catalog=master;Integrated Security=SSPI;"
    ```

    Une fois la commande exécutée, le processus génère un fichier, y compris les compteurs de performance, à l’emplacement que vous avez spécifié. Vous pouvez utiliser ce fichier comme entrée pour la partie suivante du processus, qui fournira des recommandations SKU pour les options de base de données unique et d’instances gérées.

## <a name="use-the-dma-cli-to-get-sku-recommendations"></a>Utilisation de l’interface CLI DMA pour accéder aux recommandations de référence

Utilisez le fichier de sortie des compteurs de performances que vous avez créé en tant qu’entrée pour ce processus.

Pour l’option de base de données unique, DMA fournit des recommandations pour la Azure SQL Database niveau tarifaire de base de données unique, le niveau de calcul et la taille de données maximale pour chaque base de données sur votre ordinateur. Si vous disposez de plusieurs bases de données sur votre ordinateur, vous pouvez également spécifier les bases de données pour lesquelles vous souhaitez obtenir des recommandations. DMA vous fournira également le coût mensuel estimé pour chaque base de données.

Pour Managed instance, les recommandations prennent en charge un scénario d’élévation et de décalage. En conséquence, DMA vous fournira des recommandations pour le niveau tarifaire de l’instance gérée Azure SQL Database, le niveau de calcul et la taille de données maximale pour l’ensemble des bases de données sur votre ordinateur. Là encore, si vous avez plusieurs bases de données sur votre ordinateur, vous pouvez également spécifier les bases de données pour lesquelles vous souhaitez obtenir des recommandations. DMA vous fournira également le coût mensuel estimé pour Managed instance.

Pour utiliser l’interface de ligne de commande DMA afin d’accéder aux recommandations relatives aux références SKU, à l’invite de commandes, exécutez dmacmd. exe avec les arguments suivants :

- **/Action = SkuRecommendation**: entrez cet argument pour exécuter des évaluations de références SKU.
- **/SkuRecommendationInputDataFilePath**: chemin d’accès au fichier de compteur collecté dans la section précédente.
- **/SkuRecommendationTsvOutputResultsFilePath**: le chemin d’accès pour écrire la sortie est au format TSV.
- **/SkuRecommendationJsonOutputResultsFilePath**: le chemin d’accès pour écrire les résultats de sortie au format JSON.
- **/SkuRecommendationHtmlResultsFilePath**: chemin d’accès pour écrire les résultats de sortie au format html.

En outre, sélectionnez l’un des arguments suivants :

- Empêcher l’actualisation des prix
  - **/SkuRecommendationPreventPriceRefresh**: si la valeur est true, empêche l’actualisation du prix et suppose des prix par défaut. Utilisez si l’exécution est en mode hors connexion. Si vous n’utilisez pas ce paramètre, vous devez spécifier les paramètres ci-dessous pour obtenir les derniers prix basés sur une région spécifiée.
- Procurez-vous les prix les plus récents
  - **/SkuRecommendationCurrencyCode**: devise dans laquelle afficher les prix (par exemple, « USD »).
  - **/SkuRecommendationOfferName**: nom de l’offre (par exemple, "MS-AZR-0003P"). Pour plus d’informations, consultez la page Détails de l' [offre Microsoft Azure](https://azure.microsoft.com/support/legal/offer-details/) .
    - **/SkuRecommendationRegionName**: nom de la région (par exemple, « westus »).
    - **/SkuRecommendationSubscriptionId**: ID d’abonnement.
    - **/AzureAuthenticationTenantId**: locataire d’authentification.
    - **/AzureAuthenticationClientId**: ID client de l’application AAD utilisée pour l’authentification.
    - L’une des options d’authentification suivantes :
      - Interactive
        - **AzureAuthenticationInteractiveAuthentication**: affectez la valeur true à une fenêtre indépendante d’authentification.
      - Basé sur le certificat
        - **AzureAuthenticationCertificateStoreLocation**: défini sur l’emplacement du magasin de certificats (par exemple, « CurrentUser »).
        - **AzureAuthenticationCertificateThumbprint**: définissez sur l’empreinte numérique du certificat.
      - Basé sur un jeton
        - **AzureAuthenticationToken**: définissez sur le jeton de certificat.

> [!NOTE]
> Pour obtenir le ClientId et TenantId pour l’authentification interactive, vous devez configurer une nouvelle application AAD. Pour plus d’informations sur l’authentification et l’obtention de ces informations d’identification, dans l’article [Microsoft Azure exemples de code de l’API de facturation : API RateCard](https://github.com/Azure-Samples/billing-dotnet-ratecard-api), suivez les instructions de l' **étape 1 : configurer une application cliente native dans votre locataire AAD**.

Enfin, il existe un argument facultatif que vous pouvez utiliser pour spécifier les bases de données pour lesquelles vous souhaitez obtenir des recommandations : 

- **/SkuRecommendationDatabasesToRecommend**: liste des bases de données pour lesquelles formuler des recommandations. Les noms de la base de données respectent la casse et doivent (1) se trouver dans le fichier Input. csv, (2) chaque fois qu’ils sont placés entre guillemets doubles, et (3) chacun étant séparé par un seul espace entre les noms (par exemple,/SkuRecommendationDatabasesToRecommend = "dataBase1" "Database2" "Database3"). Si vous omettez ce paramètre, assurez-vous que des recommandations sont fournies pour toutes les bases de données utilisateur identifiées dans le fichier Input. csv.  

Voici quelques exemples d’appels :

**Exemple 1 : obtention de recommandations avec des prix par défaut. Utilisez lors de l’exécution en mode hors connexion ou lorsque vous n’avez pas d’informations d’authentification.**

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true
```

**Exemple 2 : obtention de recommandations avec les derniers prix pour la région spécifiée (par exemple, « UKWest »).**

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

**Exemple 3 : obtention de recommandations pour des bases de données spécifiques (par exemple, « TPCDS1G, EDW_3G, TPCDS10G »).**

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
/SkuRecommendationDatabasesToRecommend=“TPCDS1G” “EDW_3G” “TPCDS10G” 
/AzureAuthenticationInteractiveAuthentication=true 
/AzureAuthenticationClientId=<Your AzureAuthenticationClientId> 
/AzureAuthenticationTenantId=<Your AzureAuthenticationTenantId>
```

Pour les recommandations de base de données uniques, le fichier de sortie TSV se présente comme suit :

![Fichier de base de donnée unique PowerShell affiché dans le dossier DMA](../dma/media/dma-sku-recommend-single-db-recommendations.png)

Pour les recommandations sur les instances gérées, le fichier de sortie TSV se présente comme suit :

![Fichier d’instance managée PowerShell affiché dans le dossier DMA](../dma/media/dma-sku-recommend-mi-recommendations.png)

Une description de chaque colonne dans le fichier de sortie est illustrée ci-dessous.

- **DatabaseName** : nom de votre base de données.
- **MetricType** -recommandé Azure SQL Database niveau de base de données/instance gérée unique.
- **MetricValue** -recommandé Azure SQL Database référence de base de données unique/d’instance gérée.
- **PricePerMonth** : prix estimé par mois pour la référence SKU correspondante.
- **RegionName** : nom de la région pour la référence (SKU) correspondante. 
- **IsTierRecommended** : nous faisons une recommandation de référence SKU minimale pour chaque niveau. Nous appliquons ensuite des heuristiques pour déterminer le niveau approprié pour votre base de données. Cela reflète le niveau recommandé pour la base de données. 
- **ExclusionReasons** : cette valeur est vide si un niveau est recommandé. Pour chaque niveau qui n’est pas recommandé, nous fournissons les raisons pour lesquelles il n’a pas été choisi.
- **AppliedRules** : notation abrégée des règles qui ont été appliquées.

Le niveau final recommandé (par exemple, **MetricType**) et la valeur ( **MetricValue**)-trouvé où la colonne **IsTierRecommended** est vraie-reflètent la référence SKU minimale requise pour que vos requêtes s’exécutent dans Azure avec un taux de réussite similaire à celui de vos bases de données locales. Pour Managed instance, DMA prend actuellement en charge les recommandations pour les références (SKU) 8vcore à 40vcore les plus couramment utilisées. Par exemple, si la référence SKU minimale recommandée est S4 pour le niveau standard, le fait de choisir S3 ou une version antérieure entraîne l’expiration ou l’échec de l’exécution des requêtes.

Le fichier HTML contient ces informations dans un format graphique. Il fournit un moyen convivial d’afficher la recommandation finale et d’approvisionner la partie suivante du processus. Pour plus d’informations sur la sortie HTML, reportez-vous à la section suivante.

## <a name="provision-recommended-skus-to-azure"></a>Approvisionner des références SKU recommandées sur Azure

En quelques clics, vous pouvez utiliser les recommandations identifiées pour approvisionner les références SKU cibles dans Azure vers lesquelles vous pouvez migrer vos bases de données. Vous pouvez utiliser le fichier HTML pour entrer un abonnement Azure. Choisissez le niveau tarifaire, le niveau de calcul et la taille maximale des données de vos bases de données. et générer un script pour approvisionner vos bases de données. Vous pouvez exécuter ce script à l’aide de PowerShell.

Vous pouvez effectuer ce processus sur un seul ordinateur, ou vous pouvez l’exécuter sur plusieurs ordinateurs pour déterminer les recommandations de référence SKU à l’échelle. DMA offre actuellement une expérience simple et évolutive en prenant en charge l’ensemble du processus par le biais de l’interface de ligne de commande.

Pour entrer les informations de configuration et apporter des modifications aux recommandations, mettez à jour le fichier HTML comme suit.

**Pour les recommandations relatives à une base de données unique**

![Écran de recommandations de référence SKU Azure SQL DB](../dma/media/dma-sku-recommend-single-db-recommendations1.png)

1. Ouvrez le fichier HTML et entrez les informations suivantes :
    - **ID d’abonnement** : ID d’abonnement de l’abonnement Azure auquel vous souhaitez approvisionner les bases de données.
    - **Groupe de ressources** : groupe de ressources dans lequel vous souhaitez déployer les bases de données. Entrez un groupe de ressources existant.
    - **Region** : région dans laquelle approvisionner les bases de données. Assurez-vous que votre abonnement prend en charge la région sélectionnée.
    - **Nom du serveur** : serveur Azure SQL Database sur lequel vous souhaitez déployer les bases de données. Si vous entrez un nom de serveur qui n’existe pas, il sera créé.
    - **Nom d’utilisateur** de l’administrateur : nom d’utilisateur de l’administrateur du serveur.
    - **Mot de passe d’administrateur** : mot de passe d’administrateur du serveur. Le mot de passe doit comporter au moins huit caractères et ne pas dépasser 128 caractères. Votre mot de passe doit contenir des caractères appartenant à trois des catégories suivantes : lettres majuscules, lettres minuscules, chiffres (0 à 9) et caractères non alphanumériques (!, $, #, %, etc.). Le mot de passe ne peut pas contenir la totalité ou une partie (3 + lettres consécutives) du nom d’utilisateur.

2. Passez en revue les recommandations pour chaque base de données et modifiez le niveau tarifaire, le niveau de calcul et la taille maximale des données en fonction des besoins. Veillez à désélectionner les bases de données que vous ne souhaitez pas configurer actuellement.

3. Sélectionnez **générer un script d’approvisionnement**, enregistrez le script, puis exécutez-le dans PowerShell.

    Ce processus doit créer toutes les bases de données que vous avez sélectionnées dans la page HTML.

**Pour obtenir des recommandations sur les instances gérées**

![Écran recommandations relatives aux références SKU SQL Azure MI](../dma/media/dma-sku-recommend-mi-recommendations1.png)

1. Ouvrez le fichier HTML et entrez les informations suivantes :
    - **ID d’abonnement** : ID d’abonnement de l’abonnement Azure auquel vous souhaitez approvisionner les bases de données.
    - **Groupe de ressources** : groupe de ressources dans lequel vous souhaitez déployer les bases de données. Entrez un groupe de ressources existant.
    - **Region** : région dans laquelle approvisionner les bases de données. Assurez-vous que votre abonnement prend en charge la région sélectionnée.
    - **Nom** de l’instance : instance du Managed instance Azure SQL vers lequel vous souhaitez migrer les bases de données. Le nom de l’instance ne peut contenir que des lettres minuscules, des chiffres et des « - », mais il ne peut pas commencer ou se terminer par « - » ou comporter plus de 63 caractères.
    - **Nom d’utilisateur de l’administrateur d’instance** : nom d’utilisateur de l’administrateur de l’instance. Assurez-vous que votre nom de connexion est conforme aux exigences suivantes : il s’agit d’un identificateur SQL et non d’un nom système standard (comme admin, administrateur, sa, root, dbmanager, loginmanager, etc.) ou d’un utilisateur ou d’un rôle de base de données intégré (par exemple, dbo, Guest, public, etc.). Assurez-vous que votre nom ne contient pas d’espaces, de caractères Unicode ou de caractères non alphabétiques, et qu’il ne commence pas par des chiffres ou des symboles. 
    - **Mot de passe de l’administrateur d’instance** : mot de passe d’administrateur de l’instance. Votre mot de passe doit comporter au moins 16 caractères et ne pas dépasser 128 caractères. Votre mot de passe doit contenir des caractères appartenant à trois des catégories suivantes : lettres majuscules, lettres minuscules, chiffres (0 à 9) et caractères non alphanumériques (!, $, #, %, etc.). Le mot de passe ne peut pas contenir la totalité ou une partie (3 + lettres consécutives) du nom d’utilisateur.
    - **Nom** du réseau virtuel : nom du réseau virtuel sous lequel l’instance gérée doit être approvisionnée. Entrez un nom de réseau virtuel existant.
    - **Nom du sous-** réseau : nom du sous-réseau sous lequel l’instance gérée doit être approvisionnée. Entrez un nom de sous-réseau existant.

2. Passez en revue les recommandations pour chaque instance et modifiez le niveau tarifaire, le niveau de calcul et la taille maximale des données selon vos besoins. Alors que les recommandations sont actuellement limitées à 8vcore 40vcore SKU, il est toujours possible de configurer les références SKU 64vcore et 80vcore si vous le souhaitez. Veillez à désélectionner toutes les instances que vous ne souhaitez pas configurer actuellement.

    Ce processus doit créer toutes les bases de données que vous avez sélectionnées dans la page HTML.

    > [!NOTE]
    > La création d’instances gérées sur un sous-réseau (surtout pour la première fois) peut prendre plusieurs heures. Après avoir exécuté le script de configuration via PowerShell, vous pouvez vérifier l’état de votre déploiement sur le portail Azure.

## <a name="next-step"></a>Étape suivante

- Pour obtenir la liste complète des commandes d’exécution de DMA à partir de l’interface CLI, consultez l’article [exécuter Assistant Migration de données à partir de la ligne de commande](https://docs.microsoft.com/sql/dma/dma-commandline?view=sql-server-2017).
