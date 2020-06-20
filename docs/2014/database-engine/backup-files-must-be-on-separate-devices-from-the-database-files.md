---
title: Les fichiers de sauvegarde doivent se trouver sur des appareils distincts des fichiers de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7039bebb-1f25-4cf3-81f1-393dfb78da12
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d5eff9cb3139e1e1043f99ba63d11160b1010c27
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84936144"
---
# <a name="backup-files-must-be-on-separate-devices-from-the-database-files"></a>Les fichiers de sauvegarde doivent être placés sur des périphériques distincts des fichiers de base de données
  Cette règle vérifie si les fichiers de base de données sont placés sur des périphériques distincts des fichiers de sauvegarde. Si les fichiers de base de données et les fichiers de sauvegarde sont placés sur le même périphérique et que ce dernier échoue, la base de données et ses sauvegardes ne sont pas disponibles. De la même manière, le fait de placer les fichiers de base de données et les fichiers de sauvegarde sur des périphériques distincts optimise les performances d'E/S pour l'utilisation en production de la base de données et l'écriture des sauvegardes.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Nous vous recommandons vivement de placer la base de données et les sauvegardes sur des périphériques de sauvegarde distincts.  
  
> [!NOTE]  
>  Cette stratégie ne permet pas de détecter des périphériques physiques distincts par le biais de points de montage.  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Unités de sauvegarde &#40;SQL Server&#41;](../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
 [Sauvegarder et restaurer des bases de données SQL Server](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Surveiller et appliquer les bonnes pratiques à l'aide de la Gestion basée sur des stratégies](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
