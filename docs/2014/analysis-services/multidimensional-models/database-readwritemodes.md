---
title: Base de données ReadWriteModes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], read/write
- databases [Analysis Services], read-only
ms.assetid: 03d7cb5c-7ff0-4e15-bcd2-7075d1b0dd69
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cb52c0d634a93a92d45f10c5bdeb5e2123b30106
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48082689"
---
# <a name="database-readwritemodes"></a>Base de données ReadWriteModes
  Il existe souvent des situations où un administrateur de base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (dba) souhaite modifier une base de données en lecture/écriture en une base de données en lecture seule, ou inversement. Ces situations sont souvent dues à des impératifs de fonctionnement, tels que le partage du même dossier de base de données entre plusieurs serveurs pour la montée en puissance d'une solution et l'amélioration des performances. Pour ces situations, le `ReadWriteMode` active de la propriété de base de données le [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dba facilement modifier le mode de fonctionnement de base de données.  
  
## <a name="readwritemode-database-property"></a>Propriété de base de données ReadWriteMode  
 La propriété de base de données `ReadWriteMode` spécifie si la base de données est en mode lecture/écriture ou en mode lecture seule. Ce sont les deux seules valeurs possibles de la propriété. Lorsque la base de données est en mode lecture seule, aucune modification ou mise à jour ne peut être appliquée à la base de données. Toutefois, lorsque la base de données est en mode lecture/écriture, des modifications et des mises à jour peuvent se produire. Le `ReadWriteMode` propriété de base de données est définie comme une propriété en lecture seule ; elle peut uniquement être définie via un `Attach` commande.  
  
 Quand une base de données est en mode lecture seule, certaines restrictions en vigueur affectent l'ensemble traditionnel des opérations autorisées sur la base de données. Consultez le tableau suivant pour connaître les opérations restreintes.  
  
|Mode ReadOnly (lecture seule)|Opérations restreintes|  
|-------------------|---------------------------|  
|Commandes XML/A<br /><br /> <br /><br /> Remarque : une erreur est générée quand vous exécutez l’une de ces commandes.|`Create`<br /><br /> `Alter`<br /><br /> `Delete`<br /><br /> `Process`<br /><br /> `MergePartitions`<br /><br /> `DesignAggregations`<br /><br /> `CommitTransaction`<br /><br /> `Restore`<br /><br /> `Synchronize`<br /><br /> `Insert`<br /><br /> `Update`<br /><br /> `Drop`<br /><br /> <br /><br /> Remarque : l’écriture différée de cellule est autorisée dans les bases de données définies en lecture seule ; toutefois, les modifications ne peuvent pas être validées.|  
|Instructions MDX<br /><br /> <br /><br /> Remarque : une erreur est générée quand vous exécutez l’une de ces instructions.|`COMMIT TRAN`<br /><br /> `CREATE SESSION CUBE`<br /><br /> `ALTER CUBE`<br /><br /> `ALTER DIMENSION`<br /><br /> `CREATE DIMENSION MEMBER`<br /><br /> `DROP DIMENSION MEMBER`<br /><br /> `ALTER DIMENSION`<br /><br /> <br /><br /> Remarque : Les utilisateurs Excel ne peut pas utiliser la fonctionnalité de regroupement dans les tableaux croisés dynamiques, car cette fonctionnalité est implémentée en interne à l’aide de `CREATE SESSION CUBE` commandes.|  
|Instructions DMX<br /><br /> <br /><br /> Remarque : une erreur est générée quand vous exécutez l’une de ces instructions.|`CREATE [SESSION] MINING STRUCTURE`<br /><br /> `ALTER MINING STRUCTURE`<br /><br /> `DROP MINING STRUCTURE`<br /><br /> `CREATE [SESSION] MINING MODEL`<br /><br /> `DROP MINING MODEL`<br /><br /> `IMPORT`<br /><br /> `SELECT INTO`<br /><br /> `INSERT`<br /><br /> `UPDATE`<br /><br /> `DELETE`|  
|Opérations d'arrière-plan|Les opérations d'arrière-plan qui modifieraient la base de données sont désactivées. Cela inclut le traitement différé et la mise en cache proactive.|  
  
## <a name="readwritemode-usage"></a>Utilisation de ReadWriteMode  
 La propriété de base de données `ReadWriteMode` doit être utilisée dans le cadre d'une commande de base de données `Attach`. Le `Attach` commande permet à la propriété de base de données être définie avec la valeur `ReadWrite` ou `ReadOnly`. La valeur de la propriété de base de données `ReadWriteMode` ne peut pas être mise à jour directement parce que la propriété est définie en lecture seule. Les bases de données sont créées avec la propriété `ReadWriteMode` définie avec la valeur `ReadWrite`. Une base de données ne peut pas être créée en mode lecture seule.  
  
 Pour basculer le `ReadWriteMode` propriété entre la base de données `ReadWrite` et `ReadOnly`, vous devez émettre une séquence de `Detach/Attach` commandes.  
  
 Toutes les opérations, base de données à l’exception de `Attach`, conserver le `ReadWriteMode` propriété dans son état actuel de base de données. Par exemple, les opérations telles que `Alter`, `Backup`, `Restore` et `Synchronize` conservent la valeur `ReadWriteMode`.  
  
> [!NOTE]  
>  Les cubes locaux peuvent être créés à partir d'une base de données en lecture seule.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Attacher et détacher des bases de données Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Déplacer une base de données Analysis Services](move-an-analysis-services-database.md)   
 [Élément Detach](../xmla/xml-elements-commands/detach-element.md)   
 [Attach, élément](../xmla/xml-elements-commands/attach-element.md)  
  
  
