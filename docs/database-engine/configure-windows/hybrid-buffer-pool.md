---
title: Pool de mémoires tampons hybride | Microsoft Docs
ms.custom: ''
ms.date: 11/06/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: ''
author: DBArgenis
ms.author: argenisf
manager: craigg
ms.openlocfilehash: a8098c38b72ba44ab973fe5564b93740252bafc6
ms.sourcegitcommit: 1a5448747ccb2e13e8f3d9f04012ba5ae04bb0a3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2018
ms.locfileid: "51560306"
---
# <a name="hybrid-buffer-pool"></a>Pool de mémoires tampons hybride
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Avec SQL Server 2019 CTP 2.1, une nouvelle fonctionnalité est introduite dans le moteur de base de données SQL Server qui lui permet d’accéder directement aux pages de données dans les fichiers de base de données stockés dans les appareils à mémoire persistante (PMEM). 

Dans un système traditionnel sans mémoire persistante, SQL Server met en cache les pages de données dans le pool de mémoires tampons. Avec le pool de mémoires tampons hybride, SQL Server passe outre l’exécution d’une copie de la page dans la partie DRAM du pool de mémoires tampons ; il référence la page directement sur le fichier de base de données qui réside sur un appareil PMEM. L’accès aux fichiers de données dans la mémoire PMEM pour le pool de mémoires tampons hybride est effectué à l’aide d’une opération d’E/S à mappage de mémoire, également appelée mise en compatibilité.

Seules les pages nettoyées peuvent être référencées directement sur un appareil PMEM. Quand une page est modifiée, elle est conservée dans la mémoire DRAM, puis réécrite dans l’appareil PMEM.

Cette fonctionnalité est disponible sur Windows et Linux.

## <a name="enable-hybrid-buffer-pool"></a>Activer le pool de mémoires tampons hybride

Sur CTP 2.1, vous devez activer l’indicateur de trace de démarrage 809 afin d’utiliser le pool de mémoires tampons hybride.

## <a name="best-practices-for-hybrid-buffer-pool"></a>Bonnes pratiques pour le pool de mémoires tampons hybride

* Quand vous formatez votre appareil PMEM sur Windows, utilisez la plus grande taille d’unité d’allocation disponible pour NTFS (2 Mo dans Windows Server 2019) et vérifiez que l’appareil a été activé pour DAX (DirectAccess)
  