---
title: Évaluer une entreprise et consolider les rapports d’évaluation (SQL Server) | Microsoft Docs
description: Découvrez comment utiliser le DMA pour évaluer une entreprise et consolider les rapports d’évaluation avant la mise à niveau de SQL Server ou la migration vers Azure SQL Database.
ms.custom: ''
ms.date: 03/19/2019
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
ms.author: rajpo
manager: craigg
ms.openlocfilehash: fac9636b336c2571e159c72c79d482768bf2fbe6
ms.sourcegitcommit: 0c049c539ae86264617672936b31d89456d63bb0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58618176"
---
# <a name="assess-an-enterprise-and-consolidate-assessment-reports-with-dma"></a>Évaluer une entreprise et consolider les rapports d’évaluation avec le DMA

La procédure détaillée ci-dessous vous aider à utiliser l’Assistant Migration de données pour effectuer une évaluation de mise à l’échelle réussie de mise à niveau de SQL Server sur site ou exécution de SQL Server sur des machines virtuelles Azure, ou pour la migration vers Azure SQL Database.

## <a name="prerequisites"></a>Prérequis

- Désignez un ordinateur outils sur votre réseau à partir de laquelle DMA sera lancé. Vérifiez que cet ordinateur dispose d’une connectivité à votre cible de SQL Server.
- Téléchargez et installez :
    - [Assistant Migration de données](https://www.microsoft.com/download/details.aspx?id=53595) version 3.6 ou version ultérieure.
    - [PowerShell](https://aka.ms/wmf5download) v5.0 ou version ultérieure.
    - [.NET framework](https://www.microsoft.com/download/details.aspx?id=30653) v4.5 ou version ultérieure.
    - [SSMS](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) 17.0 ou version ultérieure.
    - [Power BI desktop](https://docs.microsoft.com/power-bi/desktop-get-the-desktop).
    - [Modules Azure PowerShell](https://docs.microsoft.com/powershell/azure/install-az-ps?view=azps-1.0.0)
- Téléchargez et extrayez :
    - Le [modèle DMA rapports Power BI](https://techcommunity.microsoft.com/gxcuf89792/attachments/gxcuf89792/MicrosoftDataMigration/56/2/PowerBI-Reports.zip).
    - Le [LoadWarehouse script](https://techcommunity.microsoft.com/gxcuf89792/attachments/gxcuf89792/MicrosoftDataMigration/56/1/LoadWarehouse1.zip).

## <a name="loading-the-powershell-modules"></a>Chargement des modules PowerShell
Enregistrer les modules PowerShell dans le répertoire de modules PowerShell vous permet d’appeler les modules sans devoir les charger explicitement avant utilisation.

Pour charger les modules, procédez comme suit :
1. Accédez à C:\Program Files\WindowsPowerShell\Modules, puis créez un dossier nommé **DataMigrationAssistant**.
2. Ouvrez le [-Modules PowerShell](https://techcommunity.microsoft.com/gxcuf89792/attachments/gxcuf89792/MicrosoftDataMigration/56/3/PowerShell-Modules2.zip), puis enregistrez-les dans le dossier que vous avez créé.

      ![Modules PowerShell](../dma/media//dma-consolidatereports/dma-powershell-modules.png)

    Chaque dossier contient le fichier psm1 associé, comme indiqué dans le graphique suivant :

   ![Fichiers psm1 de modules PowerShell](../dma/media//dma-consolidatereports/dma-powershell-modules-psm1-files.png)

   > [!NOTE]
   > Le dossier et le fichier psm1 qu’il contient doivent avoir le même nom.

   > [!IMPORTANT]
   > Vous devrez peut-être débloquer les fichiers PowerShell une fois que vous les enregistrez dans le répertoire WindowsPowerShell pour vous assurer que les modules à charger correctement. Pour débloquer un fichier PowerShell, cliquez sur le fichier, sélectionnez **propriétés**, sélectionnez le **Unblock** zone de texte, puis **Ok**.

   ![Propriétés du fichier psm1](../dma/media//dma-consolidatereports/dma-psm1-file-properties.png)

    PowerShell doit maintenant se charger ces modules automatiquement au démarrage d’une nouvelle session PowerShell.

## <a name="create-inventory"></a> Créer un inventaire des serveurs SQL
Avant d’exécuter le script PowerShell afin d’évaluer vos serveurs SQL, vous devez créer un inventaire des serveurs SQL que vous souhaitez évaluer.

Cet inventaire peut prendre l’une des deux formes :
- Fichier CSV d’Excel
- Table SQL Server

### <a name="if-using-a-csv-file"></a>Si vous utilisez un fichier CSV
> [!IMPORTANT]
>
> Vérifiez que le fichier d’inventaire est enregistré dans un fichier (CSV) séparés par des virgules.
>
> Pour les instances par défaut, la valeur est le nom d’instance MSSQLServer.
>

Lorsque vous utilisez un fichier csv pour importer les données, n'assurez-vous que deux colonnes de données - **nom de l’Instance** et **nom de la base de données**, et que vous n’aient pas les lignes d’en-tête pour les colonnes.
 
 ![contenu du fichier CSV](../dma/media//dma-consolidatereports/dma-csv-file-contents.png)

### <a name="if-using-sql-server-table"></a>Si vous utilisez la table SQL Server
Créer une base de données appelée **EstateInventory** et une table appelée **DatabaseInventory**. La table contenant ces données d’inventaire peut avoir n’importe quel nombre de colonnes, tant qu’il existent quatre colonnes suivantes :
- ServerName
- InstanceName
- DatabaseName
- AssessmentFlag

![Contenu de la table SQL Server](../dma/media//dma-consolidatereports/dma-sql-server-table-contents.png)

Si cette base de données n’est pas sur l’ordinateur d’outils, assurez-vous que l’ordinateur outils dispose d’une connectivité réseau à cette instance de SQL Server.

L’avantage de l’utilisation d’une table SQL Server sur un fichier CSV est que vous pouvez utiliser la colonne d’indicateur évaluation pour contrôler l’instance / prélevés obtient pour l’évaluation, ce qui le rend plus facile de séparer les évaluations en plusieurs petits segments de base de données.  Vous pouvez, s’étendre sur plusieurs évaluations (voir la section sur l’exécution d’une évaluation plus loin dans cet article), qui est plus facile que la conservation de plusieurs fichiers CSV.

N’oubliez pas que selon le nombre d’objets et leur complexité, une évaluation peut prendre un temps exceptionnellement long (heures +), il est préférable de séparer l’évaluation en segments gérables.

## <a name="running-a-scaled-assessment"></a>Exécuter une évaluation à l’échelle
Après le chargement des modules PowerShell dans le répertoire modules et création d’un inventaire, vous devez exécuter une évaluation à l’échelle en ouvrant PowerShell et de la fonction dmaDataCollector en cours d’exécution.
 
  ![listes des fonctions dmaDataCollector](../dma/media//dma-consolidatereports/dma-dmaDataCollector-function-listing.png)

Les paramètres associés à la fonction dmaDataCollector sont décrits dans le tableau suivant.

|Paramètre  |Description |
|---------|---------|
|**getServerListFrom** | Votre inventaire. Les valeurs possibles sont **SqlServer** et **CSV**.<br/>Pour plus d’informations, consultez [créer un inventaire des serveurs SQL](#create-inventory). |
|**csvPath** | Le chemin d’accès à votre fichier d’inventaire de volume partagé de cluster.  Utilisé uniquement lorsque **getServerListFrom** a la valeur **CSV**. |
|**serverName** | Le nom de l’instance SQL Server de l’inventaire lors de l’utilisation **SqlServer** dans le **getServerListFrom** paramètre. |
|**databaseName** | La base de données qui héberge la table d’inventaire. |
|**AssessmentName** | Le nom de l’évaluation DMA. |
|**TargetPlatform** | Le type de cible d’évaluation que vous souhaitez effectuer.  Les valeurs possibles sont **AzureSQLDatabase**, **SQLServer2012**, **SQLServer2014**, **SQLServer2016**,  **SQLServerLinux2017**, **SQLServerWindows2017**, et **ManagedSqlServer**. |
|**AuthenticationMethod** | La méthode d’authentification pour la connexion aux cibles de SQL Server que vous souhaitez évaluer. Les valeurs possibles sont **SQLAuth** et **WindowsAuth**. |
|**OutputLocation** | Le répertoire dans lequel stocker le fichier JSON évaluation fichier de sortie. Selon le nombre de bases de données en cours d’évaluation et le nombre d’objets dans les bases de données, les évaluations peuvent prendre un temps exceptionnellement long. Le fichier sera écrit toutes les évaluations terminées. |

S’il existe une erreur inattendue, la fenêtre de commande qui est lancée par ce processus va être interrompue.  Passez en revue le journal des erreurs pour déterminer la raison de l’échec.
 
  ![Emplacement du journal des erreurs](../dma/media//dma-consolidatereports/dma-error-log-file-location.png)

## <a name="consuming-the-assessment-json-file"></a>Utilisation du fichier JSON d’évaluation

Une fois votre évaluation terminée, vous êtes maintenant prêt à importer les données dans SQL Server pour l’analyse. Pour utiliser le fichier JSON d’évaluation, ouvrez PowerShell et exécutez la fonction dmaProcessor.
 
  ![liste dmaProcessor (fonction)](../dma/media//dma-consolidatereports/dma-dmaProcessor-function-listing.png)

Les paramètres associés à la fonction dmaProcessor sont décrits dans le tableau suivant.

|Paramètre  |Description |
|---------|---------|
|**processTo** | L’emplacement auquel le fichier JSON sera traité. Les valeurs possibles sont **SQLServer** et **AzureSQLDatabase**. |
|**serverName** | L’instance de SQL Server à laquelle les données sont traitées.  Si vous spécifiez **AzureSQLDatabase** pour le **processTo** paramètre, puis inclure uniquement le nom de SQL Server (n’incluez pas. database.windows.net). Vous devez entrer deux connexions lors du ciblage de base de données SQL Azure ; la première est vos informations d’identification du client Azure, tandis que la deuxième est votre connexion d’administrateur pour le serveur SQL Azure. |
|**CreateDMAReporting** | La base de données intermédiaire à créer pour le traitement du fichier JSON.  Si la base de données que vous spécifiez existe et que vous définissez ce paramètre à une, les objets ne sont créés.  Ce paramètre est utile pour recréer un objet unique qui a été supprimé. |
|**CreateDataWarehouse** | Crée l’entrepôt de données qui sera utilisé par le rapport Power BI. |
|**databaseName** | Le nom de la base de données DMAReporting. |
|**warehouseName** | Le nom de la base de données de l’entrepôt de données. |
|**jsonDirectory** | Le répertoire contenant le fichier d’évaluation de JSON.  S’il existe plusieurs fichiers JSON dans le répertoire, ils sont traités un par un. |

La fonction dmaProcessor doit uniquement prendre quelques secondes pour traiter un seul fichier.

## <a name="loading-the-data-warehouse"></a>Chargement de l’entrepôt de données
Une fois la dmaProcessor a terminé le traitement des fichiers de l’évaluation, les données seront chargées dans la base de données DMAReporting dans le tableau de rapports. À ce stade, vous devez charger l’entrepôt de données.

1. Utilisez le script LoadWarehouse pour remplir des valeurs manquantes dans les dimensions.

    Le script prend les données à partir de la table de rapports dans la base de données DMAReporting et chargez-le dans l’entrepôt.  S’il existe des erreurs pendant ce processus de chargement, ils sont probablement un résultat d’entrées manquantes dans les tables de dimension.

2. Charger l’entrepôt de données.
 
      ![LoadWarehouse contenu chargé](../dma/media//dma-consolidatereports/dma-LoadWarehouse-loaded.png)

## <a name="set-your-database-owners"></a>Définir des propriétaires de votre base de données
S’il n’est pas obligatoire, pour tirer le meilleur parti des rapports, il est recommandé de définir les propriétaires de base de données le **dimDBOwner** de dimension, puis mettez à jour **DBOwnerKey** dans le  **FactAssessment** table.  Ce processus permettra de segmentation et de filtrage du rapport Power BI basé sur les propriétaires de base de données spécifique.

Vous pouvez également utiliser le script LoadWarehouse pour fournir les instructions TSQL de base pour définir les propriétaires de base de données.

  ![Propriétaires de paramètre LoadWarehouse](../dma/media//dma-consolidatereports/dma-LoadWarehouse-set-owners.png)

## <a name="dma-reports"></a>Rapports DMA

1. Ouvrez le modèle DMA rapports Power BI dans Power BI Desktop.
2. Entrez les détails du serveur qui pointent vers votre **DMAWarehouse** de base de données, puis sélectionnez **charge**.
   
      ![DMA rapports Power BI modèle chargé](../dma/media//dma-consolidatereports/dma-reports-powerbi-template-loaded.png)

   Une fois que le rapport a actualisé les données à partir de la **DMAWarehouse** base de données, vous voyez un rapport similaire à ce qui suit.

   ![Vue de rapport DMAWarehouse](../dma/media//dma-consolidatereports/dma-DMAWarehouse-report1.png)

   > [!TIP]
   > Si vous ne voyez pas les données que vous attendiez, essayez de modifier le signet actif.  Pour plus d’informations, consultez le le détail dans la section suivante.

## <a name="working-with-dma-reports"></a>Utilisation des rapports DMA
Pour utiliser les rapports DMA, utilisez signets et les segments pour filtrer par :
- Types d’évaluation (base de données SQL Azure, SQL Azure MI, SQL en local) 
- Nom d'instance
- Nom de la base de données
- Nom de l’équipe

Pour accéder au panneau de signets et les filtres, sélectionnez le signet de filtres dans la page de rapport principal :

![Filtres et les signets du rapport DMA](../dma/media//dma-consolidatereports/dma-report-bookmarks-filters.png)

Ainsi, le panneau suivant :

![Panneau des vues de rapport DMA](../dma/media//dma-consolidatereports/dma-report-views-blade.png)

Vous pouvez utiliser des signets pour basculer le contexte de création de rapports entre :
- Évaluations de cloud de base de données SQL Azure
- Évaluations de cloud Azure SQL MI
- Évaluations en local

![Signets de vues de rapport DMA](../dma/media//dma-consolidatereports/dma-report-bookmarks1.png)

Pour masquer le panneau des filtres, CTRL-clic sur le bouton précédent :

![Bouton précédent de vues de rapport DMA](../dma/media//dma-consolidatereports/dma-report-bookmarks-back.png)

Il existe une invite de commandes en bas à gauche de la page de rapport à afficher si un filtre est appliqué actuellement sur les éléments suivants :
* FactAssessment – InstanceName
* FactAssessment – DatabaseName
* dimDBOwner - DBOwner

![Invite de filtre appliqué](../dma/media//dma-consolidatereports/dma-filter-applied-prompt.png)

> [!NOTE]
> Si vous effectuez uniquement une évaluation de la base de données SQL Azure, seuls les rapports de Cloud sont remplies. À l’inverse, si vous effectuez uniquement une évaluation sur site, seuls les rapports en local sont remplies. Toutefois, si vous effectuez une application Web et une évaluation locale puis chargez les évaluations dans votre entrepôt, vous pouvez basculer entre les rapports de Cloud et sur site en cliquant sur CTRL l’icône associée.

## <a name="reports-visuals"></a>Éléments visuels de rapports
Les détails affichés dans les rapports Power BI sont indiqué dans les sections suivantes.

### <a name="readiness-"></a>% De disponibilité

  ![Pourcentage de disponibilité du DMA](../dma/media//dma-consolidatereports/dma-readiness-percentage.png)

Cet élément visuel est mis à jour en fonction du contexte de sélection (tout, de l’instance, base de données [multiples de]).

### <a name="readiness-count"></a>Nombre de préparation

  ![Nombre de préparation de DMA](../dma/media//dma-consolidatereports/dma-readiness-count.png)

Cet élément visuel affiche le nombre de bases de données qui sont prêts à migrer le nombre de bases de données qui ne sont pas encore prêt à migrer.

### <a name="readiness-bucket"></a>Compartiment de préparation

  ![Compartiment de préparation de DMA](../dma/media//dma-consolidatereports/dma-readiness-bucket.png)

Cet élément visuel montre une répartition des bases de données par les compartiments de préparation suivante :
- PRÊT DE 100 %
- 75-99 % PRÊT
- PRÊT DE 50-75 %
- NON PRÊT

### <a name="issues-word-cloud"></a>Problèmes Word Cloud
 
  ![Problèmes DMA WordCloud](../dma/media//dma-consolidatereports/dma-issues-word-cloud.png)

Cet élément visuel affiche les problèmes qui sont produisent actuellement au sein de dans le contexte de sélection (tout, de l’instance, base de données [multiples de]). Plus le mot s’affiche sur l’écran, plu le nombre de problèmes dans cette catégorie. Plaçant le pointeur de la souris sur un mot indique le nombre de problèmes qui se produisent dans cette catégorie.

### <a name="database-readiness"></a>Préparation de la base de données

  ![Rapport de disponibilité de base de données DMA](../dma/media//dma-consolidatereports/dma-database-readiness-report.png)

Cette section est la partie principale du rapport, qui affiche l’état de préparation d’une instance de la base de données. Ce rapport a une hiérarchie de zoom de :
- InstanceDatabase
- ChangeCategory
- Titre
- ObjectType
- ImpactedObjectName

 ![Analyse du rapport disponibilité de base de données DMA](../dma/media//dma-consolidatereports/dma-database-readiness-report-drilldown.png)

Ce rapport sert également le point de filtre pour la création du rapport de Plan de mise à jour.

Pour Explorer le rapport de Plan de mise à jour, avec le bouton droit sur un point de données dans ce graphique, pointez sur **extraction**, puis sélectionnez **Plans de mise à jour**.

Cette tâche filtre le rapport de plan de mise à jour au niveau de hiérarchie actuel basé sur le point à partir duquel vous sélectionnez l’option d’extraction.

  ![Disponibilité de base de données DMA analyse du rapport filtré](../dma/media//dma-consolidatereports/dma-database-readiness-report-drilldown-filtered.png)

  ![Rapport de Plan de correction DMA](../dma/media//dma-consolidatereports/dma-remediation-plan-report.png)

Vous pouvez également utiliser le rapport de Plan de correction sur le plan de son propre pour créer une mise à jour personnalisée à l’aide de filtres dans le **visualisations filtres** panneau.
 
  ![Options de filtre de rapport Plan de correction DMA](../dma/media//dma-consolidatereports/dma-remediation-plan-report-filter-options.png)

### <a name="script-disclaimer"></a>Exclusion de responsabilité de script
*Les exemples de scripts fournis dans cet article ne sont pas pris en charge par aucun programme de support standard de Microsoft ou d’un service. Tous les scripts sont fournis en l’état sans garantie d’aucune sorte. Microsoft exclut toute garantie implicite, y compris, sans limitation, une garantie implicite de qualité marchande ou d’adéquation à un usage spécifique. Vous assumez tous les risques liés à l’utilisation ou les performances des exemples de scripts et de la documentation. En aucun cas Microsoft, ses auteurs ou quiconque else impliqués dans la création, la production ou la remise des scripts est de tout dommage que ce soit (y compris, sans limitation, pertes de bénéfices, interruption d’activité, la perte de informations commerciales ou autres pertes pécuniaires) découlant de l’utilisation ou l’impossibilité d’utiliser les exemples de scripts ou la documentation, même si Microsoft a été notifié de la possibilité de tels dommages.  Recherche d’autorisation avant une nouvelle validation de ces scripts sur les autres blogs/sites/dépôts.*
