---
title: Chargement Azure SQL Data Warehouse, tâche | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPDWUPTASK.F1
- SQL11.DTS.DESIGNER.AFPDWUPTASK.F1
ms.assetid: 112cf764-f85a-4c1a-b732-d299d717c0d4
author: yualan
ms.author: chugu
ms.openlocfilehash: adcc4cc06ac01ea833972ffcd7c1a5ade411bfb2
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439316"
---
# <a name="azure-sql-dw-upload-task"></a>Tâche de chargement Azure SQL Data Warehouse
La **tâche de chargement Azure SQL Data Warehouse** permet à un package SSIS de charger des données locales sur une table dans Azure SQL Data Warehouse. Le format de fichier de données source pris en charge actuellement est le texte délimité dans l’encodage UTF-8. Le processus de chargement suit l’approche Polybase efficace. Plus précisément, les données sont tout d’abord chargées sur le stockage Blob Azure, puis sur Azure SQL Data Warehouse. Par conséquent, un compte de stockage Blob Azure est nécessaire pour utiliser cette tâche.

Pour ajouter une **tâche de chargement Azure SQL Data Warehouse**, faites-la glisser de la boîte à outils SSIS vers le canevas du concepteur, double-cliquez dessus ou cliquez dessus avec le bouton droit, puis cliquez sur **Modifier** pour afficher la boîte de dialogue de l’éditeur de tâche.

Dans la page **Général** , configurez les propriétés suivantes.

Champ|Description
-----|-----------
LocalDirectory|Spécifie le répertoire local qui contient les fichiers de données à charger.
Recursively|Spécifie s’il convient d’effectuer des recherches de façon récursive dans les sous-répertoires.
FileName|Indique un filtre de nom pour sélectionner des fichiers dont le nom répond à certains critères. Par exemple, MaFeuille*.xsl\* inclut les fichiers MaFeuille001.xsl et MaFeuilleABC.xslx.
RowDelimiter|Spécifie le ou les caractères qui marquent la fin de chaque ligne.
ColumnDelimiter|Spécifie un ou plusieurs caractères qui marquent la fin de chaque colonne. Par exemple, &#124; (barre verticale), \t (tabulation), ’ (apostrophe), “ (guillemets doubles) et 0x5c (barre oblique inverse).
IsFirstRowHeader|Spécifie si la première ligne de chaque fichier de données contient les noms de colonne au lieu des données réelles.
AzureStorageConnection|Spécifie un gestionnaire de connexions de stockage Azure.
BlobContainer|Spécifie le nom du conteneur d’objets blob sur lequel les données locales seront chargées et relayées vers Azure Data Warehouse via PolyBase. Un conteneur sera créé s’il n’existe pas.
BlobDirectory|Spécifie le répertoire d’objets blob (structure hiérarchique virtuelle) sur lequel les données locales seront chargées et relayées vers Azure Data Warehouse via PolyBase.
RetainFiles|Spécifie s’il convient de conserver les fichiers chargés sur le stockage Azure.
CompressionType|Spécifie le format de compression à utiliser lors du chargement de fichiers sur le stockage Azure. La source locale n’est pas affectée.
CompressionLevel|Spécifie le niveau de compression à utiliser pour le format de compression.
AzureDwConnection|Spécifie un gestionnaire de connexions ADO.NET pour Azure SQL Data Warehouse.
TableName|Spécifie le nom de la table de destination. Choisissez un nom de table existant ou créez-en un en choisissant **\<New Table ...>** .
TableDistribution|Spécifie la méthode de distribution pour la nouvelle table. S’applique si un nouveau nom de table est spécifié pour **TableName**.
HashColumnName|Spécifie la colonne utilisée pour la distribution de table de hachage. S’applique si la valeur **HASH** est spécifiée pour **TableDistribution**.

La page **Mappages** sera différente selon si vous procédez au chargement vers une nouvelle table ou une table existante. Dans le premier cas, configurez les colonnes sources à mapper et les noms correspondants dans la table de destination à créer. Dans le second cas, configurez les relations de mappage entre les colonnes sources et de destination.

Dans la page **Colonnes** , configurez les propriétés de type de données pour chaque colonne source.

La page **T-SQL** affiche le T-SQL utilisé pour charger des données depuis le stockage Blob Azure sur Azure SQL Data Warehouse. Le T-SQL est généré automatiquement à partir des configurations sur les autres pages et sera exécuté dans le cadre de l’exécution de la tâche. Vous pouvez choisir de modifier manuellement le T-SQL généré pour répondre à vos besoins spécifiques en cliquant sur le bouton **Modifier** . Vous pouvez revenir à celui qui a été généré automatiquement par la suite en cliquant sur le bouton **Réinitialiser** .
