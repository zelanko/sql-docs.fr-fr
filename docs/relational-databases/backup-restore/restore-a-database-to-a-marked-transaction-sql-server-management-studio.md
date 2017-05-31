---
title: "Restaurer une base de données jusqu’à une transaction marquée (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.restoretlog.markedtransaction.f1
helpviewer_keywords:
- database restores [SQL Server], marked transactions
- restoring databases [SQL Server], marked transactions
- marked transactions [SQL Server], restoring
ms.assetid: 8f0ea144-1819-4832-905f-e5d0f49b066b
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 48529229420d7c2dafad334f3104e01add1a6746
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="restore-a-database-to-a-marked-transaction-sql-server-management-studio"></a>Restaurer une base de données jusqu'à une transaction marquée (SQL Server Management Studio)
  Quand une base de données se trouve dans l’état de restauration, vous pouvez utiliser la boîte de dialogue **Restaurer le journal des transactions** pour restaurer la base de données jusqu’à une transaction marquée dans les sauvegardes du journal disponibles.  
  
> [!NOTE]  
>  Pour plus d’informations, consultez [Utiliser les transactions marquées pour récupérer des bases de données associées uniformément &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/use-marked-transactions-to-recover-related-databases-consistently.md) et [Récupération de bases de données associées contenant une transaction marquée](../../relational-databases/backup-restore/recovery-of-related-databases-that-contain-marked-transaction.md).  
  
### <a name="to-restore-a-marked-transaction"></a>Pour restaurer une transaction marquée  
  
1.  Après la connexion à l'instance appropriée du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], dans l'Explorateur d'objets, cliquez sur le nom du serveur pour développer son arborescence.  
  
2.  Développez **Bases de données**puis, selon la base de données, sélectionnez une base de données utilisateur ou développez **Bases de données système** et sélectionnez une base de données système.  
  
3.  Cliquez avec le bouton droit sur la base de données, pointez sur **Tâches**, puis cliquez sur **Restaurer**.  
  
4.  Cliquez sur **Journal des transactions**afin d’ouvrir la boîte de dialogue **Restaurer le journal des transactions** .  
  
5.  Dans la page **Général** , dans la section **Restaurer sur** , sélectionnez **Transaction marquée**afin d’ouvrir la boîte de dialogue **Sélectionner une transaction marquée** . Cette boîte de dialogue affiche une grille répertoriant les transactions marquées disponibles dans les sauvegardes du journal des transactions sélectionnées.  
  
     Par défaut, la restauration s'effectue jusqu'à la transaction marquée, en l'excluant. Pour restaurer également la transaction marquée, sélectionnez **Inclure la transaction marquée**.  
  
     Le tableau suivant répertorie les en-têtes de colonnes de la grille et décrit leur valeur.  
  
    |En-tête|Value|  
    |------------|-----------|  
    |\<vide>|Affiche une case à cocher pour la sélection de la marque.|  
    |**Marque de transaction**|Nom de la transaction marquée spécifiée par l'utilisateur lors de la validation de la transaction.|  
    |**Date**|Date et heure de la validation de la transaction. La date et l’heure de la transaction sont affichées telles qu’enregistrées dans la table **msdbgmarkhistory** , et non dans l’option Date et heure de l’ordinateur client.|  
    |**Description**|Description de la transaction marquée spécifiée par l'utilisateur lorsque la transaction a été validée (le cas échéant).|  
    |**LSN**|Numéro séquentiel dans le journal de la transaction marquée.|  
    |**Base de données**|Nom de la base de données où la transaction marquée a été validée.|  
    |**Nom d'utilisateur**|Nom de l'utilisateur de la base de données où la transaction marquée a été validée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Restaurer une sauvegarde de base de données à l’aide de SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)   
 [Restaurer une sauvegarde de journal des transactions &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
  
