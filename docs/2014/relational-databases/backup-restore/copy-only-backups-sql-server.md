---
title: Sauvegardes de type copie seule (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-backup-restore
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- copy-only backups [SQL Server]
- COPY_ONLY option [BACKUP statement]
- backups [SQL Server], copy-only backups
ms.assetid: f82d6918-a5a7-4af8-868e-4247f5b00c52
caps.latest.revision: 46
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e382d3b0bad1a5c43d6fc745280e302c9422ef0e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051973"
---
# <a name="copy-only-backups-sql-server"></a>Sauvegardes de type copie seule (SQL Server)
  Une *sauvegarde de copie uniquement* est une sauvegarde [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] indépendante du mécanisme des sauvegardes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] conventionnelles. Normalement, une sauvegarde modifie la base de données et affecte la restauration des sauvegardes ultérieures. Parfois, cependant, il est utile d'effectuer une sauvegarde à une fin précise sans affecter les procédures globales de sauvegarde et de restauration de la base de données. Pour cela, on peut recourir à une sauvegarde de copie uniquement.  
  
 Les types de sauvegarde de copie uniquement sont les suivants :  
  
-   Sauvegardes complètes de copie uniquement (tous modes de récupération)  
  
     Une sauvegarde de copie uniquement ne peut pas servir de base différentielle ni de sauvegarde différentielle et n'a aucune incidence sur la base différentielle.  
  
     La restauration d'une sauvegarde complète de copie uniquement est identique à la restauration de toute autre sauvegarde complète.  
  
-   Sauvegardes de fichier journal de copie uniquement (en mode de récupération complète et en mode de récupération utilisant les journaux de transactions uniquement)  
  
     Une sauvegarde du journal de type copie seule préserve le point d'archive du journal existant et, donc, n'a pas d'incidence sur l'ordre des sauvegardes régulières des journaux. Les sauvegardes de journaux de type copie seule sont généralement superflues. En revanche, vous pouvez créer une nouvelle sauvegarde de routine des journaux (à l'aide de WITH NORECOVERY) et utiliser cette sauvegarde conjointement avec toute sauvegarde des journaux précédente nécessaire à la séquence de restauration. Toutefois, une sauvegarde de fichier journal de copie uniquement peut parfois être utile pour effectuer une restauration en ligne. Pour obtenir un exemple, consultez [Exemple : restauration en ligne d’un fichier en lecture/écriture &#40;Mode de récupération complète&#41;](example-online-restore-of-a-read-write-file-full-recovery-model.md).  
  
     Le journal des transactions n'est jamais tronqué après une sauvegarde de type copie seule.  
  
 Les sauvegardes de copie uniquement sont enregistrées dans la colonne **is_copy_only** de la table [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) .  
  
## <a name="to-create-a-copy-only-backup"></a>Pour créer une sauvegarde de type copie uniquement  
 Vous pouvez créer une sauvegarde de copie uniquement à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou de PowerShell.  
  
###  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
1.  Sur la page **Général** de la boîte de dialogue **Sauvegarder la base de données**, sélectionnez l’option **Sauvegarde de copie uniquement**.  
  
###  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 La syntaxe [!INCLUDE[tsql](../../../includes/tsql-md.md)] essentielle est la suivante :  
  
-   Pour une sauvegarde complète de type copie uniquement :  
  
     SAUVEGARDE de base de données *nom_base_de_données* à \<backup_device*>* ... WITH COPY_ONLY …  
  
    > [!NOTE]  
    >  COPY_ONLY n'a aucun effet lorsqu'il est spécifié avec l'option DIFFERENTIAL.  
  
-   Pour une sauvegarde de fichier journal de type copie uniquement  
  
     BACKUP LOG *nom_base_de_données* TO *\<* unité_de_sauvegarde*>* … WITH COPY_ONLY …  
  
###  <a name="PowerShellProcedure"></a> Utilisation de PowerShell  
  
1.  Utilisez le `Backup-SqlDatabase` applet de commande avec le `-CopyOnly` paramètre.  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour créer une sauvegarde complète ou de fichier journal**  
  
-   [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)  
  
-   [Sauvegarder un journal des transactions &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md)  
  
 **Pour afficher des sauvegardes de copie uniquement**  
  
-   [backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql)  
  
 **Pour configurer et utiliser le fournisseur SQL Server PowerShell**  
  
-   [Fournisseur SQL Server PowerShell](../../powershell/sql-server-powershell-provider.md)  
  

  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la sauvegarde &#40;SQL Server&#41;](backup-overview-sql-server.md)   
 [Modes de récupération &#40;SQL Server&#41;](recovery-models-sql-server.md)   
 [Copier des bases de données avec la sauvegarde et la restauration](../databases/copy-databases-with-backup-and-restore.md)   
 [Vue d’ensemble de la restauration et de la récupération &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)  
  
  
