---
title: "Tâche de système de fichiers Azure Data Lake Store | Documents Microsoft"
ms.custom: 
ms.date: 08/22/2017
ms.prod: sql-server-2016
ms.reviewer: douglasl
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
ms.sourcegitcommit: 29b296b2ae7e04871e81a9c236cb990bdd19562b
ms.openlocfilehash: cbc72958f992e0b5cae12cdfc8c0996378f9708c
ms.contentlocale: fr-fr
ms.lasthandoff: 10/11/2017

---
# <a name="azure-data-lake-store-file-system-task"></a>Tâche de système de fichiers Azure Data Lake Store

La tâche de système de fichiers Azure données Lake Store permet aux utilisateurs d’effectuer diverses opérations de système de fichiers sur [Azure données Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

La tâche de système de fichiers Azure données Lake Store est un composant de la [SQL Server Integration Services (SSIS) Feature Pack pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

## <a name="configure-the-azure-data-lake-store-file-system-task"></a>Configurer la tâche de système de fichiers Azure Data Lake Store

Pour ajouter une tâche de système de fichiers Azure données Lake Store à un package, faites-le glisser à partir de la boîte à outils SSIS vers la zone de conception. Puis double-cliquez sur la tâche, ou avec le bouton droit de la tâche et sélectionnez **modifier**, pour ouvrir le **éditeur de tâche du système de fichiers Azure données Lake Store** boîte de dialogue.

Le **opération** propriété spécifie l’opération de système de fichier à exécuter. Sélectionnez une des opérations suivantes :

- **CopyToADLS :** télécharger des fichiers dans ADLS.
- **CopyFromADLS :** télécharger des fichiers à partir de ADLS.

## <a name="configure-the-properties-for-the-operation"></a>Configurer les propriétés de l’opération
Pour toute opération, vous devez spécifier un gestionnaire de connexions Azure Data Lake.

Voici les propriétés spécifiques à chaque opération :

### <a name="copytoadls"></a>CopyToADLS
- **LocalDirectory :** Spécifie le répertoire source local qui contient les fichiers à télécharger.
- **FileNamePattern :** spécifie un filtre de nom de fichier pour les fichiers sources. Seuls les fichiers dont le nom correspond au modèle spécifié sont téléchargés. Les caractères génériques `*` et `?` sont pris en charge.
- **SearchRecursively :** Spécifie s’il faut rechercher de manière récursive dans le répertoire source pour les fichiers à télécharger.
- **AzureDataLakeDirectory :** Spécifie le répertoire de destination ADLS pour télécharger des fichiers.
- **FileExpiry :** spécifie une date d’expiration et une heure pour les fichiers téléchargés vers ADLS. Laissez cette propriété vide pour indiquer que les fichiers n’expirent jamais.

### <a name="copyfromadls"></a>CopyFromADLS
- **AzureDataLakeDirectory :** Spécifie le répertoire source ADLS qui contient les fichiers à télécharger.
- **SearchRecursively :** Spécifie s’il faut rechercher de manière récursive dans le répertoire source pour les fichiers à télécharger.
- **LocalDirectory :** Spécifie le répertoire de destination pour stocker les fichiers téléchargés.
