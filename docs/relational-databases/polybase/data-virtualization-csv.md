---
title: Virtualiser des données externes dans SQL Server 2019 CTP 2.0 | Microsoft Docs
description: Cette page détaille les étapes d’utilisation de l’Assistant Création d’une table externe pour un fichier CSV
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: polybase
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 6a8ce50e4e359c8ce8dc2b0015300f9a7afb88d1
ms.sourcegitcommit: 8732161f26a93de3aa1fb13495e8a6a71519c155
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71710608"
---
# <a name="use-the-external-table-wizard-with-csv-files"></a>Utiliser l’Assistant Table externe avec des fichiers CSV

SQL Server 2019 permet également de virtualiser les données d’un fichier CSV dans HDFS.  Ce processus permet aux données de rester à leur emplacement d’origine et de les **virtualiser** dans une instance SQL Server, ce qui vous permet de les interroger comme n’importe quelle autre table dans SQL Server. Cette fonctionnalité évite ainsi de recourir à des processus ETL. Ceci est possible via l’utilisation de connecteurs PolyBase. Pour plus d’informations sur la virtualisation des données, consultez notre document [Bien démarrer avec PolyBase](polybase-guide.md).

## <a name="prerequisite"></a>Condition préalable

À compter de CTP 2.4, le pool de données et les sources de données externes du pool de stockage ne sont plus créés par défaut dans votre cluster de Big Data. Avant d’utiliser l’Assistant, créez la source de données externe **SqlStoragePool** par défaut dans votre base de données cible à l’aide de la requête Transact-SQL suivante. N’oubliez pas de changer d’abord le contexte de la requête à votre base de données cible.

```sql
-- Create default data sources for SQL Big Data Cluster
IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlDataPool')
    CREATE EXTERNAL DATA SOURCE SqlDataPool
    WITH (LOCATION = 'sqldatapool://controller-svc/default');

IF NOT EXISTS(SELECT * FROM sys.external_data_sources WHERE name = 'SqlStoragePool')
    CREATE EXTERNAL DATA SOURCE SqlStoragePool
    WITH (LOCATION = 'sqlhdfs://controller-svc/default');
```

## <a name="launch-the-external-table-wizard"></a>Lancer l’Assistant Table externe

Connectez-vous à la racine HDFS à l’aide de l’adresse IP. Développez les éléments dans l’Explorateur d’objets. Sélectionnez ensuite l’un des fichiers CSV dont vous voulez virtualiser les données en une instance SQL Server existante. Cliquez avec le bouton droit sur le fichier, puis sélectionnez **Créer une table externe à partir d’un fichier CSV** dans le menu contextuel. Vous pouvez également créer des tables externes des fichiers CSV d’un dossier dans HDFS, si les fichiers en question respectent le même schéma. Cela permet la virtualisation des données au niveau des dossiers, sans nécessiter le traitement de chaque fichier ou l’obtention d’un jeu de résultats joints à partir des données combinées. Ceci lance l’Assistant Virtualisation de données. Vous pouvez également lancer l’Assistant Virtualisation de données à partir de la palette de commandes en appuyant sur les touches Ctrl+Maj+P (sur Windows) ou Cmd+Maj+P (sur Mac).

![Assistant Virtualisation de données](media/data-virtualization/csv-virtualize-data-wizard.png)

## <a name="connect-to-a-sql-server-master-instance"></a>Se connecter à une instance maître de SQL Server

Ici, vous pouvez spécifier quelle instance maître SQL vous allez également connecter à l’aide des informations concernant l’adresse IP, le port et les informations d’identification. Les connexions précédemment enregistrées sont accessibles via la zone de liste déroulante **Connexions SQL Server actives**. 
> [!NOTE]
>Si vous utilisez une connexion enregistrée, les autres champs seront bloqués.


![Sélectionner une source de données](media/data-virtualization/csv-connect-to-master.png)

Cliquez sur Suivant pour passer à l’étape suivante de l’Assistant, qui permet de définir la clé principale de la base de données.

## <a name="select-destination-database"></a>Sélectionner la base de données de destination

Dans cette étape, vous allez choisir la base de données de destination dans laquelle virtualiser les données. Le champ de liste déroulante contient toutes les bases de données acceptables de l’instance maître SQL, spécifiée dans l’écran précédent. Ici, vous pouvez également nommer la nouvelle table externe et voir le schéma qu’elle utilisera.

![Créer une clé principale de base de données](media/data-virtualization/csv-select-destination.png)


## <a name="preview-data"></a>Aperçu des données

Dans cette fenêtre, vous pourrez avoir un aperçu des 50 premières lignes de votre fichier CSV afin de les valider.

Une fois terminé, cliquez sur « Suivant » pour continuer.

![Informations d’identification de la source de données externe](media/data-virtualization/csv-preview-data.png)

## <a name="modify-columns"></a>Modifier les colonnes

Dans la fenêtre suivante, vous pourrez modifier les colonnes de la table externe que vous avez l’intention de créer. Vous pouvez modifier le nom de la colonne, modifier le type des données et autoriser les lignes Nullable. 

![Informations d’identification de la source de données externe](media/data-virtualization/csv-modify-columns.png)


## <a name="summary"></a>Résumé

Cette étape fournit un récapitulatif de vos sélections. Elle fournit des informations sur l’instance maître SQL et sur la table externe proposée. Dans cette étape, vous pouvez choisir **Générer un script** avec la syntaxe en T-SQL nécessaire pour créer la source de données externe ou **Créer**, qui crée l’objet de source de données externe.

![Écran Récapitulatif](media/data-virtualization/csv-virtualize-data-summary.png)

Si vous cliquez sur « Créer », vous pourrez voir la table externe créée dans la base de données de destination.

![Sources de données externes](media/data-virtualization/csv-external-data-sources.png)

Si vous cliquez sur **Générer un script**, vous voyez que la requête T-SQL est générée pour créer l’objet de source de données externe.

![Générer un script](media/data-virtualization/csv-generated-script.png)

> [!NOTE]
> L’option Générer un script doit normalement être visible seulement dans la dernière page de l’Assistant. Actuellement, elle apparaît dans toutes les pages.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur SQL Server Big Data Cluster et les scénarios associés, consultez [Qu’est-ce que SQL Server Big Data Cluster ?](../../big-data-cluster/big-data-cluster-overview.md).
