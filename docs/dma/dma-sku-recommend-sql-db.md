---
title: Identifier la référence SKU à base de données SQL Azure appropriée pour votre base de données locale (Data Migration Assistant) | Microsoft Docs
description: Découvrez comment utiliser l’Assistant de Migration de données pour identifier le droit SKU de base de données SQL Azure pour votre base de données locale
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
manager: jroth
ms.openlocfilehash: 5effd31d37af5fbe119f1ad23781b994fa89c240
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794321"
---
# <a name="identify-the-right-azure-sql-databasemanaged-instance-sku-for-your-on-premises-database"></a>Identifier la référence (SKU) de Azure SQL Database/Managed Instance droite pour votre base de données locale

Bases de données de migration vers le cloud peuvent être compliquées, en particulier lorsque vous tentez de sélectionner le meilleur cible de base de données Azure et de la référence (SKU) pour votre base de données. Notre objectif avec la base de données de Migration Assistant (DMA) est de vous aider à résoudre ces problèmes et faciliter votre migration de base de données en fournissant ces recommandations de référence (SKU) dans une sortie conviviale.

Cet article se concentre sur la fonctionnalité de recommandations de DMA SKU de base de données SQL Azure. Base de données SQL Azure a plusieurs options de déploiement, y compris :

- Base de données unique
- Pools élastiques
- instance managée

Les recommandations de référence (SKU) fonctionnalité vous permet d’identifier les deux la valeur minimale recommandée d’Azure SQL database unique ou une instance gérée référence (SKU) en fonction des compteurs de performances collectés à partir des ou les ordinateurs hébergeant vos bases de données. La fonctionnalité fournit des recommandations relatives à la tarification du niveau, de niveau de calcul et de taille maximale de données, ainsi que coût estimé par mois. Il offre également la possibilité pour les bases de données en bloc approvisionner uniques et des instances gérées dans Azure pour toutes les bases de données recommandées.

> [!NOTE]
> Cette fonctionnalité est actuellement disponible uniquement via l’Interface de ligne de commande (CLI).

Vous trouverez ci-dessous des instructions pour vous aider à déterminer les recommandations de référence de base de données SQL Azure et configurer des bases de données unique correspondant ou des instances gérées dans Azure à l’aide de DMA.

## <a name="prerequisites"></a>Prérequis

- Téléchargez et installez la dernière version de [DMA](https://aka.ms/get-dma). Si vous avez déjà une version antérieure de l’outil, ouvrez-le et vous êtes invité à mettre à niveau le DMA.
- Assurez-vous que votre ordinateur dispose [PowerShell Version 5.1](https://www.microsoft.com/download/details.aspx?id=54616) ou version ultérieure, qui est requise pour exécuter tous les scripts. Pour plus d’informations sur findoug les version de PowerShell est installée sur votre ordinateur, consultez l’article [télécharger et installer Windows PowerShell 5.1](https://docs.microsoft.com/skypeforbusiness/set-up-your-computer-for-windows-powershell/download-and-install-windows-powershell-5-1).
- Assurez-vous que votre ordinateur dispose du Module Azure Powershell installé. Pour plus d’informations, consultez l’article [installer le module Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-1.8.0).
- Vérifiez que le fichier PowerShell **SkuRecommendationDataCollectionScript.ps1**, qui est nécessaire pour collecter les compteurs de performances, est installé dans le dossier DMA.
- Assurez-vous que l’ordinateur sur lequel vous allez effectuer ce processus dispose des autorisations d’administrateur sur l’ordinateur qui héberge vos bases de données.

## <a name="collect-performance-counters"></a>Collecter les compteurs de performances

La première étape du processus consiste à collecter les compteurs de performances de vos bases de données. Vous pouvez collecter les compteurs de performances en exécutant une commande PowerShell sur l’ordinateur qui héberge vos bases de données. DMA vous fournit une copie de ce fichier de PowerShell, mais vous pouvez également utiliser votre propre méthode pour capturer les compteurs de performances de votre ordinateur.

Vous n’avez pas besoin effectuer cette tâche pour chaque base de données individuellement. Les compteurs de performances collectées à partir d’un ordinateur peuvent être utilisés pour recommander la référence (SKU) pour toutes les bases de données hébergées sur l’ordinateur.

1. Dans le dossier DMA, localisez le fichier PowerShell SkuRecommendationDataCollectionScript.ps1. Ce fichier est nécessaire pour collecter les compteurs de performances.

    ![Fichier PowerShell indiqué dans le dossier DMA](../dma/media/dma-sku-recommend-data-collection-file.png)

2. Exécutez le script PowerShell avec les arguments suivants :
    - **ComputerName**: Le nom de l’ordinateur qui héberge vos bases de données.
    - **OutputFilePath**: Chemin d’accès du fichier de sortie pour enregistrer les compteurs collectés.
    - **CollectionTimeInSeconds**: La durée pendant laquelle vous souhaitez collecter des données de compteur de performances. Capturer les compteurs de performance pour au moins 40 minutes obtenir une recommandation éloquent. Plus la durée de la capture, plus précises la recommandation sera. Vérifiez également que les charges de travail sont en cours d’exécution pour les bases de données de votre choisis activer les recommandations plus précises.
    - **DbConnectionString**: La chaîne de connexion pointant vers la base de données principale hébergée sur l’ordinateur à partir de laquelle vous collectez des données de compteur de performances.

    Voici un exemple d’appel :

    ```
    .\SkuRecommendationDataCollectionScript.ps1
     -ComputerName Foobar1
     -OutputFilePath D:\counters2.csv
     -CollectionTimeInSeconds 2400
     -DbConnectionString "Server=localhost;Initial Catalog=master;Integrated Security=SSPI;"
    ```

    Une fois la commande exécutée, le processus génère un fichier, y compris les compteurs de performances à l’emplacement spécifié. Vous pouvez utiliser ce fichier en tant qu’entrée pour la partie suivante du processus, qui fournit des recommandations de référence (SKU) pour la base de données unique et options d’instances gérées.

## <a name="use-the-dma-cli-to-get-sku-recommendations"></a>Utiliser CLI DMA pour obtenir des recommandations de référence (SKU)

Utiliser le fichier de sortie de compteurs de performances que vous avez créé en tant qu’entrée pour ce processus.

Pour l’option de base de données unique, DMA des recommandations sur la base de données Azure SQL Database unique niveau tarifaire, le niveau de calcul et la taille maximale des données pour chaque base de données sur votre ordinateur. Si vous avez plusieurs bases de données sur votre ordinateur, vous pouvez également spécifier les bases de données pour laquelle vous souhaitez que les recommandations. DMA également vous fournira le coût mensuel estimé pour chaque base de données.

Pour l’instance managée, les recommandations prennent en charge un scénario de lift-and-shift. Par conséquent, DMA vous fournira les recommandations pour l’instance gérée Azure SQL Database niveau tarifaire, le niveau de calcul et la taille maximale des données pour l’ensemble des bases de données sur votre ordinateur. Là encore, si vous avez plusieurs bases de données sur votre ordinateur, vous pouvez également spécifier les bases de données pour laquelle vous souhaitez que les recommandations. DMA également vous fournira le coût mensuel estimé pour l’instance managée.

Pour utiliser la CLI DMA pour obtenir des recommandations de référence (SKU), à l’invite de commandes, exécutez dmacmd.exe avec les arguments suivants :

- **/ Action = SkuRecommendation**: Entrez cet argument pour exécuter des évaluations de la référence (SKU).
- **/SkuRecommendationInputDataFilePath**: Le chemin d’accès au fichier de compteur sont collectées dans la section précédente.
- **/SkuRecommendationTsvOutputResultsFilePath**: Le chemin d’accès pour écrire les résultats de sortie au format TSV.
- **/SkuRecommendationJsonOutputResultsFilePath**: Le chemin d’accès pour écrire les résultats de sortie au format JSON.
- **/SkuRecommendationHtmlResultsFilePath**: Chemin d’accès pour écrire les résultats de sortie au format HTML.

En outre, sélectionnez un des arguments suivants :

- Empêcher l’actualisation de prix
  - **/SkuRecommendationPreventPriceRefresh**: Si la valeur est True, empêche l’actualisation de prix et part du principe que les prix par défaut. Utilisez si en cours d’exécution en mode hors connexion. Si vous n’utilisez pas ce paramètre, vous devez spécifier les paramètres ci-dessous pour obtenir les prix les plus récents basés sur une région spécifiée.
- Obtenir les derniers cours
  - **/SkuRecommendationCurrencyCode**: La devise dans laquelle afficher les prix (par exemple) « USD »).
  - **/SkuRecommendationOfferName**: Nom de l’offre (par exemple) "MS-AZR-0003P"). Pour plus d’informations, consultez le [détails de l’offre Microsoft Azure](https://azure.microsoft.com/support/legal/offer-details/) page.
    - **/SkuRecommendationRegionName**: Le nom de la région (par exemple, « WestUS »).
    - **/SkuRecommendationSubscriptionId**: L'ID de l'abonnement.
    - **/AzureAuthenticationTenantId**: Le client d’authentification.
    - **/AzureAuthenticationClientId**: L’ID client de l’application AAD utilisée pour l’authentification.
    - L’une des options d’authentification suivantes :
      - Interactif
        - **AzureAuthenticationInteractiveAuthentication**: La valeur true pour une fenêtre contextuelle d’authentification.
      - Basée sur les certificats
        - **AzureAuthenticationCertificateStoreLocation**: La valeur est l’emplacement du magasin de certificats (par exemple, « CurrentUser »).
        - **AzureAuthenticationCertificateThumbprint**: La valeur est l’empreinte numérique du certificat.
      - Jeton basé
        - **AzureAuthenticationToken**: Définir sur le jeton de certificat.

> [!NOTE]
> Pour obtenir les valeurs ClientId et l’ID de locataire pour l’authentification interactive, vous devez configurer une nouvelle application AAD. Pour plus d’informations sur l’authentification et l’obtention de ces informations d’identification, dans l’article [exemples de Code de API de facturation Microsoft Azure : L’API RateCard](https://azure.microsoft.com/resources/samples/billing-python-ratecard-api/), suivez les instructions sous **étape 1 : Configurer une application cliente Native dans votre client AAD**.

Enfin, il est un argument facultatif, que vous pouvez utiliser pour spécifier les bases de données pour laquelle vous souhaitez que les recommandations : 

- **/SkuRecommendationDatabasesToRecommend**: Une liste de bases de données pour lequel faire des recommandations. La base de données noms respectent la casse et devront (1) se trouve dans le fichier .csv d’entrée, (2) chacune être entouré de guillemets doubles, et (3) être séparés par un seul espace entre les noms (par exemple, /SkuRecommendationDatabasesToRecommend = « Database1 » « Database2 » « Database3 ») . L’omission de ce paramètre vous assurer que les recommandations sont fournies pour toutes les bases de données utilisateur identifiés dans le fichier .csv d’entrée.  

Voici certains appels de l’exemple :

**Exemple 1 : Obtention de recommandations avec les prix par défaut. Utiliser lors de l’exécution en mode hors connexion ou lorsque vous n’avez pas les informations d’identification de l’authentification.**

```
.\DmaCmd.exe /Action=SkuRecommendation
/SkuRecommendationInputDataFilePath="C:\TestOut\out.csv"
/SkuRecommendationTsvOutputResultsFilePath="C:\TestOut\prices.tsv"
/SkuRecommendationJsonOutputResultsFilePath="C:\TestOut\prices.json"
/SkuRecommendationOutputResultsFilePath="C:\TestOut\prices.html"
/SkuRecommendationPreventPriceRefresh=true
```

**Exemple 2 : Obtention de recommandations avec les prix les plus récents pour la région spécifiée (par exemple, « UKWest »).**

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

**Exemple 3 : Obtention de recommandations pour les bases de données spécifiques (par exemple) « TPCDS1G, EDW_3G, TPCDS10G »).**

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

Pour obtenir des recommandations de base de données unique, le fichier de sortie TSV se présentera comme suit :

![Fichier de base de données unique PowerShell indiqué dans le dossier DMA](../dma/media/dma-sku-recommend-single-db-recommendations.png)

Pour des recommandations de l’instance gérée, le fichier de sortie TSV se présentera comme suit :

![Fichier d’instance gérée PowerShell indiqué dans le dossier DMA](../dma/media/dma-sku-recommend-mi-recommendations.png)

Une description de chaque colonne dans le fichier de sortie suit.

- **DatabaseName** -le nom de votre base de données.
- **MetricType** -recommandé de base de données SQL Azure unique base de données gérés/niveau de l’instance.
- **MetricValue** -recommandé de base de données SQL Azure unique base de données gérés/référence (SKU) de l’instance.
- **PricePerMonth** – prix estimé par mois pour la référence (SKU) correspondante.
- **RegionName** – le nom de la région de la référence (SKU) correspondante. 
- **IsTierRecommended** -nous nous assurons une recommandation de référence (SKU) minimale pour chaque niveau. Nous appliquons ensuite les paramètres heuristiques pour déterminer le niveau approprié pour votre base de données. Cela reflète le niveau est recommandé pour la base de données. 
- **ExclusionReasons** -cette valeur est vide si un niveau est recommandé. Pour chaque niveau qui n’est pas recommandé, nous fournissons les raisons pourquoi il n’a pas été récupéré.
- **AppliedRules** -une notation courte des règles qui ont été appliquées.

Le niveau recommandé final (par exemple, **MetricType**) et la valeur (par exemple, **MetricValue**)-trouvé où le **IsTierRecommended** colonne est TRUE - reflète la référence (SKU) minimale requis pour vos requêtes à exécuter dans Azure avec un taux de réussite semblable à vos bases de données sur site. Pour l’instance managée, DMA prend actuellement en charge les recommandations pour les plus couramment utilisés 8vcore à 40vcore références (SKU). Par exemple, si la référence (SKU) minimale recommandée est S4 pour le niveau standard, puis en choisissant S3 ci-dessous sera provoquer l’expiration du délai des requêtes ou ne parviennent pas à exécuter.

Le fichier HTML contient ces informations dans un format graphique. Il fournit un moyen convivial d’affichage de la recommandation finale et de la partie suivante du processus d’approvisionnement. Plus d’informations sur la sortie HTML est dans la section suivante.

## <a name="provision-recommended-skus-to-azure"></a>Configuration recommandée des références (SKU) vers Azure

Avec seulement quelques clics, vous pouvez utiliser les recommandations fournies à approvisionner cible références SKU dans Azure à laquelle vous pouvez migrer vos bases de données. Vous pouvez utiliser le fichier HTML à l’entrée d’abonnement Azure ; choisir le niveau tarifaire, le calcul de niveau et la taille maximale des données pour vos bases de données ; et générer un script pour configurer vos bases de données. Vous pouvez exécuter ce script à l’aide de PowerShell.

Vous pouvez effectuer ce processus sur un seul ordinateur, ou vous pouvez effectuer cette opération sur plusieurs ordinateurs afin de déterminer les recommandations de référence (SKU) à grande échelle. DMA actuellement rend une expérience simple et évolutive en prenant en charge l’ensemble du processus via l’Interface de ligne de commande.

Pour entrer les informations de configuration et apporter des modifications aux recommandations, mettez à jour le fichier HTML comme suit.

**Pour obtenir des recommandations de base de données unique**

![Écran de recommandations de référence (SKU) de base de données SQL Azure](../dma/media/dma-sku-recommend-single-db-recommendations1.png)

1. Ouvrez le fichier HTML et entrez les informations suivantes :
    - **ID d’abonnement** -l’ID d’abonnement de l’abonnement Azure auquel vous souhaitez approvisionner les bases de données.
    - **Groupe de ressources** -le groupe de ressources auquel vous souhaitez déployer les bases de données. Entrez un groupe de ressources existant.
    - **Région** -la région dans laquelle configurer les bases de données. Assurez-vous que votre abonnement prend en charge de la zone de sélection.
    - **Nom du serveur** -server de la base de données Azure SQL auquel vous souhaitez que les bases de données déployées. Si vous entrez un nom de serveur qui n’existe pas, il sera créé.
    - **Admin Username** -le nom d’utilisateur administrateur de serveur.
    - **Mot de passe administrateur** -le mot de passe administrateur serveur. Le mot de passe doit être au moins huit caractères et pas plus de 128 caractères. Votre mot de passe doit contenir des caractères appartenant à trois des catégories suivantes : lettres majuscules des lettres, des lettres minuscules, des chiffres (0-9) et des caractères non alphanumériques ( !, $, #, %, etc..). Le mot de passe ne peut pas contenir tout ou partie (3 + lettres consécutives) à partir du nom d’utilisateur.

2. Passez en revue les recommandations pour chaque base de données et modifier le niveau tarifaire, niveau et la taille de données max en fonction des besoins de calcul. Veillez à désélectionner les bases de données que vous ne souhaitez pas actuellement à approvisionner.

3. Sélectionnez **générer un Script d’approvisionnement**, enregistrez le script, puis l’exécuter dans PowerShell.

    Ce processus doit créer les bases de données que vous avez sélectionné dans la page HTML.

**Pour obtenir des recommandations instance managée**

![Écran de recommandations de référence (SKU) de MI SQL Azure](../dma/media/dma-sku-recommend-mi-recommendations1.png)

1. Ouvrez le fichier HTML et entrez les informations suivantes :
    - **ID d’abonnement** -l’ID d’abonnement de l’abonnement Azure auquel vous souhaitez approvisionner les bases de données.
    - **Groupe de ressources** -le groupe de ressources auquel vous souhaitez déployer les bases de données. Entrez un groupe de ressources existant.
    - **Région** -la région dans laquelle configurer les bases de données. Assurez-vous que votre abonnement prend en charge de la zone de sélection.
    - **Nom de l’instance** – l’instance d’Azure SQL Managed Instance à laquelle vous souhaitez migrer les bases de données. Le nom d’instance peut contenir uniquement des lettres minuscules, chiffres, et '-', mais il ne peut pas commencer ou finir par '-' ou comporter plus de 63 caractères.
    - **Instance Admin Username** – le nom d’utilisateur administrateur d’instance. Assurez-vous que votre nom de connexion respecte les exigences suivantes : c’est un identificateur SQL et pas un nom système type (comme admin, administrateur, sa, root, dbmanager, loginmanager, etc.), ou un utilisateur de base de données intégré ou un rôle (comme dbo, guest, public, etc.). Assurez-vous que votre nom ne contient des espaces blancs, des caractères Unicode ou des caractères non alphabétiques, et qu’il ne commence pas par des chiffres ou des symboles. 
    - **Mot de passe administrateur de l’instance** -le mot de passe administrateur instance. Votre mot de passe doit être au moins 16 caractères et pas plus de 128 caractères. Votre mot de passe doit contenir des caractères appartenant à trois des catégories suivantes : lettres majuscules des lettres, des lettres minuscules, des chiffres (0-9) et des caractères non alphanumériques ( !, $, #, %, etc..). Le mot de passe ne peut pas contenir tout ou partie (3 + lettres consécutives) à partir du nom d’utilisateur.
    - **Nom du réseau virtuel** – nom du réseau virtuel le sous lequel l’instance managée doit être configurée. Entrez un nom de réseau virtuel existant.
    - **Nom du sous-réseau** – nom du sous-réseau The sous lequel l’instance managée doit être configurée. Entrez un nom de sous-réseau existant.

2. Passez en revue les recommandations pour chaque instance et modifier le niveau tarifaire, niveau et la taille de données max en fonction des besoins de calcul. Bien que les recommandations sont actuellement limitées aux 8vcore aux références SKU 40vcore, il existe toujours l’option permettant d’approvisionner les références (SKU) 64vcore et 80vcore si vous le souhaitez. Veillez à désélectionner toutes les instances que vous ne souhaitez pas actuellement à approvisionner.

    Ce processus doit créer les bases de données que vous avez sélectionné dans la page HTML.

    > [!NOTE]
    > Création d’instances gérées sur un sous-réseau (en particulier pour la première fois) peut prendre plusieurs heures. Après avoir exécuté le script de configuration via PowerShell, vous pouvez vérifier l’état de votre déploiement sur le portail Azure.

## <a name="next-step"></a>Étape suivante

- Pour obtenir une liste complète des commandes utilisées pour exécuter le DMA à partir de l’interface CLI, consultez l’article [exécuter Data Migration Assistant à partir de la ligne de commande](https://docs.microsoft.com/sql/dma/dma-commandline?view=sql-server-2017).
