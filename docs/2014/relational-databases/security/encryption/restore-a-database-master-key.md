---
title: Restaurer une clé principale de base de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-security
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- database master key [SQL Server], importing
ms.assetid: 16897cc5-db8f-43bb-a38e-6855c82647cf
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2d2608be4f4691e8b0279def055f838fe94006b8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140710"
---
# <a name="restore-a-database-master-key"></a>Restaurer une clé principale de base de données
  Cette rubrique décrit la restauration de la clé principale de base de données dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   [Pour restaurer la clé principale de base de donnée à l'aide de Transact-SQL](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Une fois la clé principale restaurée, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] déchiffre toutes les clés chiffrées au moyen de la clé principale active, puis chiffre ces clés au moyen de la clé principale restaurée. Cette opération gourmande en ressources doit être planifiée au cours d'une période de faible demande. Si la clé principale de base de données en cours n'est pas ouverte ou ne peut pas être ouverte, ou si une clé chiffrée à l'aide de cette clé principale ne peut pas être déchiffrée, l'opération de restauration échoue.  
  
-   Si l'un des déchiffrements échoue, la restauration échoue. Vous pouvez utiliser l'option FORCE pour ignorer les erreurs, mais cette option entraîne la perte de toutes les données ne pouvant pas être déchiffrées.  
  
-   Si la clé principale a été chiffrée à l'aide de la clé principale du service, la clé principale restaurée sera également chiffrée à l'aide de la clé principale du service.  
  
-   S'il n'existe aucune clé principale dans la base de données en cours, l'instruction RESTORE MASTER KEY crée une clé principale. La nouvelle clé principale n'est pas automatiquement chiffrée au moyen de la clé principale du service.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert l'autorisation CONTROL sur la base de données.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio avec Transact-SQL  
  
#### <a name="to-restore-the-database-master-key"></a>Pour restaurer la clé principale de base de données  
  
1.  Récupérez une copie de la clé principale de base de données sauvegardée, à partir d'un support de sauvegarde physique ou d'un répertoire sur le système de fichiers local.  
  
2.  Dans l'**Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
3.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
4.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Restores the database master key of the AdventureWorks2012 database.  
    USE AdventureWorks2012;  
    GO  
    RESTORE MASTER KEY   
        FROM FILE = 'c:\backups\keys\AdventureWorks2012_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003#GHkf02597gheij04'   
        ENCRYPTION BY PASSWORD = '259087M#MyjkFkjhywiyedfgGDFD';  
    GO  
    ```  
  
    > [!NOTE]  
    >  Le chemin d'accès à la clé et le mot de passe de la clé (s'il existe) seront différents de ce qui est indiqué ci-dessus. Assurez-vous que les deux sont spécifiques à votre installation de serveur et de clé.  
  
 Pour plus d’informations, consultez [RESTORE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-master-key-transact-sql)  
  
  
