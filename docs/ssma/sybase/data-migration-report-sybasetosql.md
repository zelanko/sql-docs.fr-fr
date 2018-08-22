---
title: Rapport de Migration de données (SybaseToSQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: bac234ef-bc16-47e6-8a7c-aa6e76d860c5
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 9e1f04f6a5df77be0bfc13227e1033842b5dd291
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "40394644"
---
# <a name="data-migration-report-sybasetosql"></a>Rapport de migration des données (SybaseToSQL)
Le **rapport de Migration de données** boîte de dialogue apparaît une fois que vous migrez des données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="options"></a>Options  
**État**  
Affiche l’état de la migration de données à partir de la source vers la base de données cible.  
  
**From**  
La table source.  
  
**Pour**  
La table cible.  
  
**Nombre total de lignes**  
Le nombre de lignes de données dans la table source.  
  
**Nombre de lignes a été migrées**  
Le nombre de lignes de données migrés avec succès à la table cible.  
  
**Ratio**  
Le pourcentage de lignes migrés avec succès.  
  
**Détails**  
En cas d’échec de la migration des données, cliquez pour afficher les détails de la migration de la ligne sélectionnée dans le rapport. SSMA affichera la raison de l’échec.  
  
**Enregistrer le rapport**  
Enregistre le rapport à un. CSV, fichier (valeurs séparées par des virgules), qui peut être examiné à l’aide de Microsoft Excel.  
  
