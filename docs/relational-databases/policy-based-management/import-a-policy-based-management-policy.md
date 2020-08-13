---
title: Importer une stratégie de gestion basée sur des stratégies | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, import policy
ms.assetid: 850b7ef9-d2b7-4754-bf04-7cb419ffb776
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 54e0ca12595b0ce8bdde128c9261918c910ffdcf
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87934345"
---
# <a name="import-a-policy-based-management-policy"></a>Importer une stratégie de gestion basée sur des stratégies
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Cette rubrique explique comment importer une instance de stratégie de gestion basée sur des stratégies dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="permissions"></a>Autorisations
 Nécessite l'appartenance au rôle PolicyAdministratorRole dans la base de données msdb.

  
##  <a name="using-sql-server-management-studio"></a>Utilisation de SQL Server Management Studio  
  
### <a name="to-import-a-policy-instance"></a>Pour importer une instance de stratégie  
  
1.  Dans **l’Explorateur d’objets**, cliquez sur le signe plus (+) pour développer le serveur où l’instance de stratégie importée résidera.  
  
2.  Cliquez sur le signe plus (+) pour développer le dossier **Gestion** .  
  
3.  Cliquez sur le signe plus (+) pour développer **Gestion de la stratégie**.  
  
4.  Cliquez avec le bouton droit sur le dossier **Stratégies** et sélectionnez **Importer une stratégie**.  
  
5.  Dans la boîte de dialogue **Importer** , tapez le nom et le chemin du fichier ou utilisez le bouton Parcourir (**...**) pour rechercher et sélectionner le fichier XML qui contient la stratégie. Pour plus d'informations sur les options disponibles dans la boîte de dialogue **Importer** , consultez [Import Policies Dialog Box](../../relational-databases/policy-based-management/import-policies-dialog-box.md).  
  
6.  Lorsque vous avez terminé, cliquez sur **OK**.  


## <a name="example-policies"></a>Exemples de stratégies
 Les exemples de stratégies ne sont pas inclus dans le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], mais des exemples de stratégies distribuées précédemment sont accessibles en installant [SQL Server Management Studio v17](../../ssms/release-notes-ssms.md#previous-ssms-releases).  Une fois SQL Server Management Studio v17 installé, vous trouverez des exemples de stratégies dans `C:\Program Files (x86)\Microsoft SQL Server\140\Tools\Policies`. Ces stratégies peuvent être importées et utilisées comme base pour vos propres stratégies de gestion basée sur des stratégies.
