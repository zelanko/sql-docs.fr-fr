---
description: MSSQLSERVER_1803
title: MSSQLSERVER_1803 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1803 (Database Engine error)
ms.assetid: d4315390-82f1-4c4c-8d1b-1a4989537cca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5a1e652d3ccf32a85fc0c1299f54c00a34ea06fb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456352"
---
# <a name="mssqlserver_1803"></a>MSSQLSERVER_1803
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|1803|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|NO_SPACE|  
|Texte du message|Échec de CREATE DATABASE. Le fichier primaire doit être doté d’une capacité minimale de %d Mo pour recevoir une copie de la base de données model.|  
  
## <a name="explanation"></a>Explication  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] crée une base de données en effectuant une copie de la base de données model. Ensuite, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] renomme la copie et agrandit la nouvelle base de données à la taille demandée. Dans le cas présent, l'utilisateur a essayé de créer une base de données plus petite que la base de données model. L'opération a échoué car la copie de la base de données model ne correspondait pas au fichier de données primaire, parce que le fichier était plus petit que la base de données model.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Créez la base de données en utilisant une plus grande taille pour le fichier de base de données. Réduisez ensuite si vous le souhaitez la base de données en utilisant [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou l'instruction DBCC SHRINKDATABASE.  
  
