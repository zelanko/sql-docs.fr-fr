---
title: Détecter des problèmes de carte hôte SCSI | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 75225b64-c102-4f1b-888a-fe72710dbfcd
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: a4dc33b9fa7b6f48f1012d3a4e6442aa0f3a8370
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85654549"
---
# <a name="detect-scsi-host-adapter-issues"></a>Détecter des problèmes de carte hôte SCSI
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette règle recherche l’ID d’événement 1066 dans le journal des événements système. Cette erreur est due à des problèmes de configuration de l'adaptateur hôte SCSI ou au mauvais fonctionnement d'un périphérique.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Pour plus d'informations sur la résolution de cette erreur, consultez l'article suivant de la Base de connaissances Microsoft :  
  
-   [Article 311081 de la Base de connaissances Microsoft](https://go.microsoft.com/fwlink/?linkid=117744)  
  
  
