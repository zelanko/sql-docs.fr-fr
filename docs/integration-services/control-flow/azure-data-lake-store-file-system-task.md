---
title: "Tâche de système de fichiers Azure Data Lake Store | Documents Microsoft"
ms.custom: 
ms.date: 08/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: Lingxi-Li
ms.author: lingxl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 303d3b74da3fe370d19b7602c0e11e67b63191e7
ms.openlocfilehash: ce2355de312faed9ab66991d6d0dd344ff315a55
ms.contentlocale: fr-fr
ms.lasthandoff: 08/29/2017

---
# <a name="azure-data-lake-store-file-system-task"></a>Tâche de système de fichiers Azure Data Lake Store

Le **lac de données Azure Store File System Task** permet aux utilisateurs d’effectuer diverses opérations de système de fichiers sur [Azure données Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

Le **lac de données Azure Store File System Task** est un composant de la [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Pour ajouter une tâche de système de fichiers Azure données Lake Store à un package, faites-le glisser à partir de la boîte à outils SSIS vers la zone de conception. Puis double-cliquez sur la tâche, ou avec le bouton droit de la tâche et sélectionnez **modifier**pour ouvrir la boîte de dialogue de l’éditeur de tâche.

Le **opération** propriété spécifie l’opération de système de fichier à exécuter. Les opérations suivantes sont prises en charge.

* **CopyToADLS :** télécharger des fichiers dans ADLS.
* **CopyFromADLS :** télécharger des fichiers à partir de ADLS.

Pour toute opération, vous devez spécifier un gestionnaire de connexions Azure Data Lake.

Voici les descriptions des propriétés spécifiques à chaque opération.

## <a name="copytoadls"></a>CopyToADLS
* **LocalDirectory :** Spécifie le répertoire source qui contient les fichiers à télécharger.
* **FileNamePattern :** spécifie un filtre de nom de fichier pour les fichiers sources. Seuls les fichiers dont le nom correspond au modèle spécifié seront téléchargés. Les caractères génériques `*` et `?` sont pris en charge.
* **SearchRecursively :** Spécifie s’il faut rechercher de manière récursive dans le répertoire source pour les fichiers à télécharger.
* **AzureDataLakeDirectory :** Spécifie le répertoire de destination ADLS pour télécharger des fichiers.
* **FileExpiry :** spécifie une date d’expiration et l’heure pour les fichiers téléchargement vers ADLS, ou laissez cette propriété vide pour indiquer que les fichiers n’expirent jamais.

## <a name="copyfromadls"></a>CopyFromADLS
* **AzureDataLakeDirectory :** Spécifie le répertoire source ADLS qui contient les fichiers à télécharger.
* **SearchRecursively :** Spécifie s’il faut rechercher de manière récursive dans le répertoire source pour les fichiers à télécharger.
* **LocalDirectory :** Spécifie le répertoire de destination pour stocker les fichiers téléchargés.
