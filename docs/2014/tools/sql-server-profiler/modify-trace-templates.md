---
title: Modifier des modèles de Trace | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
helpviewer_keywords:
- templates [SQL Server], SQL Server Profiler
- Profiler [SQL Server Profiler], templates
- trace templates [SQL Server]
- modifying trace templates
- SQL Server Profiler, templates
ms.assetid: 75b62a54-8d16-4599-bd2d-c42cfcc209f4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ebe8924f46de15a3a34c0f49304c87a904919bdb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63035036"
---
# <a name="modify-trace-templates"></a>Modifier des modèles de trace
  Vous pouvez modifier les modèles enregistrés dans un fichier sur l'ordinateur local sur lequel le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] est en cours d'exécution. Vous pouvez également modifier les modèles dérivés de ces fichiers. Quand vous modifiez des modèles existants, vous modifiez leurs propriétés, telles que les classes d’événements et les colonnes de données, en suivant l’ordre de la définition initiale des propriétés, sous l’onglet **Sélection des événements** de la boîte de dialogue **Propriétés de la trace** . Les classes d'événements et les colonnes de données peuvent être ajoutées ou supprimées, et les filtres peuvent être modifiés. Une fois le modèle modifié, un modèle spécifique à l'utilisateur est créé et le modèle système initial demeure intact. Pour plus d’informations, consultez [Enregistrer des traces et des modèles de trace](save-traces-and-trace-templates.md).  
  
 Il se peut que vous deviez dériver un modèle d'un fichier de trace existant si vous ne vous rappelez pas (ou si n'avez pas effectué d'enregistrement) du modèle d'origine utilisé pour créer la trace, ou bien si vous voulez exécuter la même trace à une date ultérieure. Lorsque vous utilisez des traces existantes, vous pouvez afficher les propriétés, mais pas les modifier. Pour modifier les propriétés, arrêtez ou suspendez la trace. Pour plus d’informations, consultez [Dériver un modèle à partir d’un fichier de trace ou d’une table de trace &#40;SQL Server Profiler&#41;](sql-server-profiler.md) et [Dériver un modèle à partir d’une trace en cours d’exécution &#40;SQL Server Profiler&#41;](derive-a-template-from-a-running-trace-sql-server-profiler.md).  
  
 **Pour créer un modèle de trace**  
  
 [Créer un modèle de trace &#40;SQL Server Profiler&#41;](create-a-trace-template-sql-server-profiler.md)  
  
 **Pour exécuter une trace à partir d'un modèle de trace**  
  
 [Créer une trace &#40;SQL Server Profiler&#41;](create-a-trace-sql-server-profiler.md)  
  
 **Pour modifier un modèle de trace**  
  
 [Utilisation de SQL Server Profiler](../../database-engine/modify-a-trace-template-sql-server-profiler.md)  
  
 [Utilisation de Transact-SQL](../../relational-databases/sql-trace/modify-an-existing-trace-transact-sql.md)  
  
 **Pour ajouter ou supprimer des événements dans un modèle de trace ou un fichier de trace**  
  
 [Utilisation de SQL Server Profiler](specify-events-and-data-columns-for-a-trace-file-sql-server-profiler.md)  
  
 [Utilisation de Transact-SQL](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer une trace](start-a-trace.md)  
  
  
