---
title: Les fichiers de sauvegarde doivent être placés sur des périphériques distincts des fichiers de base de données
description: Découvrez comment activer une stratégie pour vérifier l’emplacement du fichier de sauvegarde par rapport à celui du fichier de base de données pour la gestion basée sur une stratégie avec SQL Server.
ms.custom: seo-lt-2019
ms.date: 08/31/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 5b98f8163a3564ccc4aadac6c71c30eb5cf37697
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89285065"
---
# <a name="backup-files-must-be-on-separate-devices-from-the-database-files"></a>Les fichiers de sauvegarde doivent être placés sur des périphériques distincts des fichiers de base de données
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette règle vérifie si les fichiers de base de données sont placés sur des périphériques distincts des fichiers de sauvegarde. Si les fichiers de base de données et les fichiers de sauvegarde sont placés sur le même périphérique et que ce dernier échoue, la base de données et ses sauvegardes ne sont pas disponibles. De la même manière, le fait de placer les fichiers de base de données et les fichiers de sauvegarde sur des périphériques distincts optimise les performances d'E/S pour l'utilisation en production de la base de données et l'écriture des sauvegardes.  
  
## <a name="best-practices-recommendations"></a>Bonnes pratiques recommandées  
 À titre de recommandation, il est préférable que le disque de sauvegarde ne soit pas le même que les disques de données ou de journal de la base de données. Ce paramètre est primordial pour garantir l'accès aux sauvegardes en cas d'échec du disque de données ou de journal.

Si les fichiers de base de données et les fichiers de sauvegarde sont placés sur le même périphérique et que ce dernier échoue, la base de données et ses sauvegardes ne sont pas disponibles. De la même manière, le fait de placer les fichiers de base de données et les fichiers de sauvegarde sur des périphériques distincts optimise les performances d'E/S pour l'utilisation en production de la base de données et l'écriture des sauvegardes.
  
## <a name="see-also"></a>Voir aussi 
   
  
 [Unités de sauvegarde](../backup-restore/backup-devices-sql-server.md)  
  
