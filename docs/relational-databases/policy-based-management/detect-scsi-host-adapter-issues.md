---
description: Détecter des problèmes de carte hôte SCSI
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
ms.openlocfilehash: 8617d6aba180ff6089e61eb00df1dca509905eb9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88406465"
---
# <a name="detect-scsi-host-adapter-issues"></a>Détecter des problèmes de carte hôte SCSI
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette règle recherche l’ID d’événement 1066 dans le journal des événements système. Cette erreur est due à des problèmes de configuration de l'adaptateur hôte SCSI ou au mauvais fonctionnement d'un périphérique.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
 Pour plus d'informations sur la résolution de cette erreur, consultez l'article suivant de la Base de connaissances Microsoft :  
  
-   [Article 311081 de la Base de connaissances Microsoft](https://go.microsoft.com/fwlink/?linkid=117744)  
  
  
