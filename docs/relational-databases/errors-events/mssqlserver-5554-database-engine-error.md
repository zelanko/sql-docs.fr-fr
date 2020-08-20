---
description: MSSQLSERVER_5554
title: MSSQLSERVER_5554 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5554 (Database Engine error)
ms.assetid: 7134bbe5-d240-4a98-85ce-b13cc8ae9b0e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f8039ad4a6cfefcdbd4e72c583f520e36f273875
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470899"
---
# <a name="mssqlserver_5554"></a>MSSQLSERVER_5554
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|MSSQLSERVER|  
|ID de l’événement|5554|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|FS_MINIVER_OVERFLOW|  
|Texte du message|La limite maximale du nombre total de versions d'un seul fichier pour le système de fichiers a été atteinte.|  
  
## <a name="explanation"></a>Explication  
Dans les scénarios de déclencheur ou MARS (Multiple Active Result Set), [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise la miniversion spécifiée par le système d’exploitation.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Essayez d'éviter les mises à jour répétées des données dans la même transaction.  
  
