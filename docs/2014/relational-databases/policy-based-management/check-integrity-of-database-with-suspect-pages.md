---
title: Vérifier l’intégrité d’une base de données contenant des pages suspectes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
caps.latest.revision: 10
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3ef41e61871541be7f8c0aff77a9136e807d91ea
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43820065"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a>Vérifier l'intégrité d'une base de données contenant des pages suspectes
  Cette règle recherche les bases de données utilisateur dont l'état de base de données a la valeur suspect. Lorsque le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] lit une page de la base de données contenant une erreur 824, cette page est jugée suspecte, son ID est enregistré dans la table suspect_pages dans msdb et la base de données contenant cette page prend la valeur suspecte.  
  
 L'erreur 824 indique qu'une erreur de cohérence logique a été détectée au cours d'une opération de lecture. Cette erreur indique généralement que des données ont été endommagées par un composant défectueux du sous-système d'E/S. Il s'agit d'une condition d'erreur grave qui menace l'intégrité de la base de données et qui doit être immédiatement corrigée.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
  
-   Examinez les détails de l'erreur 824 pour cette base de données dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Effectuez une vérification complète de la cohérence de la base de données ([DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)).  
  
-   Implémentez les actions utilisateur définies dans [MSSQLSERVER_824](http://go.microsoft.com/fwlink/?LinkId=81397).  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Gérer la table suspect_pages &#40;SQL Server&#41;](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
