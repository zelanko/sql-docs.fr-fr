---
title: Système de fichiers Azure Data Lake Store, tâche | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f1b3fc1317e4454008a628c03e189e690bfeb21d
ms.sourcegitcommit: 1f53b6a536ccffd701fc87e658ddac714f6da7a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54206275"
---
# <a name="azure-data-lake-store-file-system-task"></a>Système de fichiers Azure Data Lake Store, tâche

Le **tâche de système de fichiers Azure Data Lake Store** permet aux utilisateurs d’effectuer diverses opérations de système de fichiers sur [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

Pour ajouter une tâche de système de fichiers Azure Data Lake Store à un package, faites-la glisser depuis la boîte à outils SSIS vers la zone de conception. Double-cliquez sur la tâche, ou avec le bouton droit de la tâche, puis sélectionnez **modifier**pour ouvrir la boîte de dialogue de l’éditeur de tâche.

La propriété **Opération** indique l’opération de système de fichiers à réaliser. Les opérations suivantes sont prises en charge.

* **CopyToADLS :** Charger des fichiers vers ADLS.
* **CopyFromADLS :** Téléchargez les fichiers depuis ADLS.

Pour toute opération, vous devez spécifier un gestionnaire de connexions Azure Data Lake.

Voici les descriptions des propriétés spécifiques à chaque opération.

## <a name="copytoadls"></a>CopyToADLS

* **LocalDirectory :** Spécifie le répertoire source qui contient les fichiers à charger.
* **FileNamePattern :** Spécifie un filtre de nom de fichier pour les fichiers sources. Charger uniquement les fichiers dont le nom correspond au modèle spécifié. Les caractères génériques `*` et `?` sont pris en charge.
* **SearchRecursively :** Spécifie s’il faut rechercher de manière récursive dans le répertoire source des fichiers à charger.
* **AzureDataLakeDirectory :** Spécifie le répertoire de destination ADLS charger les fichiers.
* **FileExpiry :** Spécifie une date d’expiration et une heure pour les fichiers chargés dans ADLS, ou laissez cette propriété vide pour indiquer que les fichiers n’expirent jamais.

## <a name="copyfromadls"></a>CopyFromADLS

* **AzureDataLakeDirectory :** Spécifie le répertoire source ADLS qui contient les fichiers à télécharger.
* **SearchRecursively :** Spécifie s’il faut rechercher de manière récursive dans le répertoire source des fichiers à télécharger.
* **LocalDirectory :** Spécifie le répertoire de destination pour stocker les fichiers téléchargés.
