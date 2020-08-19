---
description: MSSQLSERVER_17128
title: MSSQLSERVER_17128 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1902d498a93555957b0c240d349a951327086382
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88410985"
---
# <a name="mssqlserver_17128"></a>MSSQLSERVER_17128
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|17128|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|INIT_NOBUFSPACE|  
|Texte du message|initdata : aucune mémoire pour les tampons du noyau.|  
  
## <a name="explanation"></a>Explication  
Les réservations ou les allocations de mémoire initiales du pool de mémoires tampons ont échoué, et SQL Server se termine.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Provoqué généralement par le démarrage de SQL Server sur un ordinateur extrêmement petit, beaucoup plus petit que la configuration requise minimale.  
  
