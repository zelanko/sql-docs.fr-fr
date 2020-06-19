---
title: Système de fichiers Azure Data Lake Store, tâche | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.AFPADLSTASK.F1
- SQL11.DTS.DESIGNER.AFPADLSTASK.F1
ms.assetid: 02b9edd7-6ef9-463e-abbf-e1830bcae875
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 30002ff43f841aa52ed809f217d3549cc64a768b
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84925354"
---
# <a name="azure-data-lake-store-file-system-task"></a>Système de fichiers Azure Data Lake Store, tâche

La **tâche de système de fichiers Azure Data Lake Store** permet aux utilisateurs d’effectuer diverses opérations de système de fichiers sur [Azure Data Lake Store (ADLS)](https://azure.microsoft.com/services/data-lake-store/).

Pour ajouter une tâche de système de fichiers Azure Data Lake Store à un package, faites-la glisser depuis la boîte à outils SSIS vers la zone de conception. Double-cliquez ensuite sur la tâche, ou cliquez avec le bouton droit sur la tâche et sélectionnez **modifier**pour ouvrir la boîte de dialogue Éditeur de tâche.

La propriété **Opération** indique l’opération de système de fichiers à réaliser. Les opérations suivantes sont prises en charge.

* **CopyToADLS :** charger des fichiers dans ADLS.
* **CopyFromADLS :** télécharger des fichiers depuis ADLS.

Pour toute opération, vous devez spécifier un gestionnaire de connexions Azure Data Lake.

Voici les descriptions des propriétés spécifiques à chaque opération.

## <a name="copytoadls"></a>CopyToADLS

* **LocalDirectory :** Spécifie le répertoire source qui contient les fichiers à charger.
* **FileNamePattern :** spécifie un filtre de nom de fichier pour les fichiers sources. Seuls les fichiers dont le nom correspond au modèle spécifié seront téléchargés. Les caractères génériques `*` et `?` sont pris en charge.
* **SearchRecursively :** indique si des fichiers à charger doivent être recherchés de manière récursive dans le répertoire source.
* **AzureDataLakeDirectory :** spécifie le répertoire de destination ADLS dans lequel charger les fichiers.
* **FileExpiry :** Spécifie une date et une heure d’expiration pour les fichiers téléchargés sur ADLS, ou laissez cette propriété vide pour indiquer que les fichiers n’expirent jamais.

## <a name="copyfromadls"></a>CopyFromADLS

* **AzureDataLakeDirectory :** spécifie le répertoire source ADLS qui contient les fichiers à télécharger.
* **SearchRecursively :** indique si des fichiers à télécharger doivent être recherchés de manière récursive dans le répertoire source.
* **LocalDirectory :** spécifie le répertoire de destination dans lequel stocker les fichiers téléchargés.
