---
title: Inscrire un serveur cible dans un serveur maître | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- enlisting target servers [SQL Server]
- SQL Server Agent jobs, target servers
- master servers [SQL Server], enlisting target servers
- SQL Server Agent jobs, master servers
- target servers [SQL Server], enlisting
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 298a3045cc9fc51664c77fcc28d89c95d30fd6fe
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48085629"
---
# <a name="enlist-a-target-server-to-a-master-server"></a>Inscrire un serveur cible dans un serveur maître
  Cette rubrique explique comment ajouter des serveurs cibles à une configuration d'administration multiserveur. Exécutez la procédure suivante à partir du serveur maître : dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)], ou d'objets SMO (SQL Server Management Objects).  
  
 Pour plus d’informations sur la manière dont le compte Windows utilisé pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent affecte un environnement multiserveur, consultez [Créer un environnement multi-serveur](create-a-multiserver-environment.md).  
  
 Le chiffrement SSL (Secure Sockets Layer) complet et la validation de certificats sont activés pour les connexions entre les serveurs maîtres et les serveurs cible par défaut. Pour plus d’informations, consultez [Définir des options de chiffrement sur des serveurs cibles](set-encryption-options-on-target-servers.md).  
  
 **Dans cette rubrique**  
  
-   **Pour inscrire un serveur cible à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SMO](#PowerShellProcedure)  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-enlist-a-target-server"></a>Pour inscrire un serveur cible  
  
1.  Dans l' **Explorateur d'objets**, développez un serveur configuré en tant que serveur maître.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent**, pointez sur **Administration multiserveur**, puis cliquez sur **Ajouter des serveurs cibles**.  
  
3.  Exécutez l'Assistant Création d'un serveur cible, qui vous guide tout au long du processus.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-enlist-a-target-server"></a>Pour inscrire un serveur cible  
  
1.  Utilisez la procédure stockée `sp_msx_enlist`.  Pour plus d’informations, consultez [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql)  
  
##  <a name="PowerShellProcedure"></a> À l’aide de SQL Server Management Objects (SMO)  
  
## <a name="see-also"></a>Voir aussi  
 [Administration automatisée à l'échelle d'une entreprise](automated-administration-across-an-enterprise.md)  
  
  
