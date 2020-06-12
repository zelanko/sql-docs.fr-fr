---
title: ReadWriteModes de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], read/write
- databases [Analysis Services], read-only
ms.assetid: 03d7cb5c-7ff0-4e15-bcd2-7075d1b0dd69
author: minewiskan
ms.author: owend
ms.openlocfilehash: 723eb7c1c0e8547ee411fc54ecd4aca613011b38
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547111"
---
# <a name="database-readwritemodes"></a>Base de données ReadWriteModes
  Il existe souvent des situations où un administrateur de base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (dba) souhaite modifier une base de données en lecture/écriture en une base de données en lecture seule, ou inversement. Ces situations sont souvent dues à des impératifs de fonctionnement, tels que le partage du même dossier de base de données entre plusieurs serveurs pour la montée en puissance d'une solution et l'amélioration des performances. Dans ces situations, la `ReadWriteMode` propriété de base de données permet à l’administrateur de base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] de modifier facilement le mode de fonctionnement de la base de données.  
  
## <a name="readwritemode-database-property"></a>Propriété de base de données ReadWriteMode  
 La propriété de base de données `ReadWriteMode` spécifie si la base de données est en mode lecture/écriture ou en mode lecture seule. Ce sont les deux seules valeurs possibles de la propriété. Lorsque la base de données est en mode lecture seule, aucune modification ou mise à jour ne peut être appliquée à la base de données. Toutefois, lorsque la base de données est en mode lecture/écriture, des modifications et des mises à jour peuvent se produire. La propriété de base de données `ReadWriteMode` est définie comme une propriété en lecture seule ; elle ne peut être définie qu'à travers une commande `Attach`.  
  
 Quand une base de données est en mode lecture seule, certaines restrictions en vigueur affectent l'ensemble traditionnel des opérations autorisées sur la base de données. Consultez le tableau suivant pour connaître les opérations restreintes.  
  
|Mode ReadOnly (lecture seule)|Opérations restreintes|  
|-------------------|---------------------------|  
|Commandes XML/A<br /><br /> <br /><br /> Remarque : une erreur est générée quand vous exécutez l’une de ces commandes.|`Create`<br /><br /> `Alter`<br /><br /> `Delete`<br /><br /> `Process`<br /><br /> `MergePartitions`<br /><br /> `DesignAggregations`<br /><br /> `CommitTransaction`<br /><br /> `Restore`<br /><br /> `Synchronize`<br /><br /> `Insert`<br /><br /> `Update`<br /><br /> `Drop`<br /><br /> <br /><br /> Remarque : l’écriture différée de cellule est autorisée dans les bases de données définies en lecture seule ; toutefois, les modifications ne peuvent pas être validées.|  
|Instructions MDX<br /><br /> <br /><br /> Remarque : une erreur est générée quand vous exécutez l’une de ces instructions.|`COMMIT TRAN`<br /><br /> `CREATE SESSION CUBE`<br /><br /> `ALTER CUBE`<br /><br /> `ALTER DIMENSION`<br /><br /> `CREATE DIMENSION MEMBER`<br /><br /> `DROP DIMENSION MEMBER`<br /><br /> `ALTER DIMENSION`<br /><br /> <br /><br /> Remarque : les utilisateurs Excel ne peuvent pas utiliser la fonctionnalité de regroupement dans les tableaux croisés dynamiques, car cette fonctionnalité est implémentée en interne à l’aide des commandes `CREATE SESSION CUBE`.|  
|Instructions DMX<br /><br /> <br /><br /> Remarque : une erreur est générée quand vous exécutez l’une de ces instructions.|`CREATE [SESSION] MINING STRUCTURE`<br /><br /> `ALTER MINING STRUCTURE`<br /><br /> `DROP MINING STRUCTURE`<br /><br /> `CREATE [SESSION] MINING MODEL`<br /><br /> `DROP MINING MODEL`<br /><br /> `IMPORT`<br /><br /> `SELECT INTO`<br /><br /> `INSERT`<br /><br /> `UPDATE`<br /><br /> `DELETE`|  
|Opérations en arrière-plan|Les opérations d'arrière-plan qui modifieraient la base de données sont désactivées. Cela inclut le traitement différé et la mise en cache proactive.|  
  
## <a name="readwritemode-usage"></a>Utilisation de ReadWriteMode  
 La propriété de base de données `ReadWriteMode` doit être utilisée dans le cadre d'une commande de base de données `Attach`. La commande `Attach` permet que la propriété de base de données soit définie avec la valeur `ReadWrite` ou la valeur `ReadOnly`. La valeur de la propriété de base de données `ReadWriteMode` ne peut pas être mise à jour directement parce que la propriété est définie en lecture seule. Les bases de données sont créées avec la propriété `ReadWriteMode` définie avec la valeur `ReadWrite`. Une base de données ne peut pas être créée en mode lecture seule.  
  
 Pour faire basculer la `ReadWriteMode` propriété de la base de données entre `ReadWrite` et `ReadOnly` , vous devez émettre une séquence de `Detach/Attach` commandes.  
  
 Toutes les opérations de base de données, à l'exception d'`Attach`, conservent la propriété de base de données `ReadWriteMode` dans son état courant. Par exemple, les opérations telles que `Alter`, `Backup`, `Restore` et `Synchronize` conservent la valeur `ReadWriteMode`.  
  
> [!NOTE]  
>  Les cubes locaux peuvent être créés à partir d'une base de données en lecture seule.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.Server.Attach%2A>   
 <xref:Microsoft.AnalysisServices.Database.Detach%2A>   
 [Attacher et détacher des bases de données Analysis Services](attach-and-detach-analysis-services-databases.md)   
 [Déplacer une base de données Analysis Services](move-an-analysis-services-database.md)   
 [Détacher l’élément](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/detach-element)   
 [Élément Attach](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/attach-element)  
  
  
