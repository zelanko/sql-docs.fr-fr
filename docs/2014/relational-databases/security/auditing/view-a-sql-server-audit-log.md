---
title: Afficher un journal d’audit SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- audits [SQL Server], viewing logs
- viewing audit logs
- logs [SQL Server], audit
ms.assetid: e8feaca0-7852-422b-895a-319b965d8d9b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: fa30824e32faae5feee1612305c1ca292d44e8e4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63012018"
---
# <a name="view-a-sql-server-audit-log"></a>Afficher un journal d'audit SQL Server
  Cette rubrique explique comment afficher un journal d'audit SQL Server dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher un journal d'audit SQL Server, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l’autorisation `CONTROL SERVER`.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-a-sql-server-audit-log"></a>Pour afficher un journal d'audit SQL Server  
  
1.  Dans l'Explorateur d'objets, développez le dossier **Sécurité** .  
  
2.  Développez le dossier **Audits** .  
  
3.  Cliquez avec le bouton droit sur le journal d’audit que vous souhaitez afficher et sélectionnez **Afficher les journaux d’audit**. La boîte **de dialogue visionneuse du fichier journal-**_SERVER_NAME_ s’ouvre. Pour plus d'informations, consultez [Log File Viewer F1 Help](../../logs/log-file-viewer-f1-help.md).  
  
4.  Lorsque vous avez terminé, cliquez sur **Fermer**.  
  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] recommande d'afficher le journal d'audit à l'aide de la visionneuse du fichier journal. Toutefois, si vous créez un système de surveillance automatisé, les informations contenues dans le fichier d’audit peuvent être lues directement à l’aide de la fonction [sys.fn_get_audit_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-get-audit-file-transact-sql). Si le fichier est lu directement, les données sont retournées dans un format légèrement différent (non traité). Pour plus d’informations **, consultez sys. fn_get_audit_file**  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Audit &#40moteur de base de données&#41;](sql-server-audit-database-engine.md)   
 [Écrire des événements d’audit SQL Server dans le journal de sécurité](write-sql-server-audit-events-to-the-security-log.md)  
  
  
