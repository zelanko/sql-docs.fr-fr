---
title: Flexible File Task | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPEXTFILETASK.F1
- SQL14.DTS.DESIGNER.AFPEXTFILETASK.F1
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2d01304a36f7676f53ffef3f6c6e3c600cb87cb6
ms.sourcegitcommit: fc0eb955b41c9c508a1fe550eb5421c05fbf11b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66411096"
---
# <a name="flexible-file-task"></a>Flexible File Task

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Flexible File Task permet aux utilisateurs d’effectuer des opérations de fichiers sur divers services de stockage pris en charge.
Les services de stockage actuellement pris en charge sont :

- Système de fichiers local
- [Stockage Blob Azure](https://azure.microsoft.com/services/storage/blobs/)
- [Azure Data Lake Storage Gen2](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-introduction)

Flexible File Task est un composant du [Feature Pack SQL Server Integration Services (SSIS) pour Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Pour ajouter une tâche Flexible File Task à un package, faites-la glisser de la boîte à outils SSIS vers la zone de conception. Ensuite, double-cliquez sur la tâche, ou cliquez dessus avec le bouton droit et sélectionnez **Modifier**, pour ouvrir la boîte de dialogue **Flexible File Task Editor**.

La propriété **Operation** indique l’opération de fichier à réaliser.
Seule l’opération **Copy** est actuellement prise en charge.

Pour l’opération **Copy**, les propriétés suivantes sont disponibles.

- **SourceConnectionType :** spécifie le type de gestionnaire de connexions source.
- **SourceConnection :** spécifie le gestionnaire de connexions source.
- **SourceFolderPath :** spécifie le chemin du dossier source.
- **SourceFileName :** spécifie le nom du fichier source. Si ce champ est vide, le dossier source sera copié.
- **SearchRecursively :** spécifie s’il faut copier les sous-dossiers de manière récursive.
- **DestinationConnectionType :** spécifie le type de gestionnaire de connexions de destination.
- **DestinationConnection :** spécifie le gestionnaire de connexions de destination.
- **DestinationFolderPath :** spécifie le chemin du dossier de destination.
- **DestinationFileName :** spécifie le nom du fichier de destination.
