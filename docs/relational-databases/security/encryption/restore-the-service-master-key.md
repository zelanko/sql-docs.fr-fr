---
title: "Restaurer la clé principale du service | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service master key [SQL Server], importing
- service master key [SQL Server], restoring
ms.assetid: 14bdbbbe-d384-4692-b670-4243d2466fe1
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 341662ff65d44b63738b869999ab78191f991a6f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="restore-the-service-master-key"></a>Restaurer la clé principale du service
  Cette rubrique explique comment restaurer la clé principale de service dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
> [!WARNING]  
>  Il est peu probable que vous ayez jamais à restaurer cette clé. Si vous deviez le faire, observez la plus grande prudence. Pour plus d’informations, consultez [Back Up the Service Master Key](../../../relational-databases/security/encryption/back-up-the-service-master-key.md).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   [Pour restaurer la clé principale de service à l'aide de Transact-SQL](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Lorsque la clé principale de service est restaurée, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] déchiffre toutes les clés et les secrets qui ont été chiffrés au moyen de la clé principale de service en cours, puis les chiffre au moyen de la clé principale de service chargée à partir du fichier de sauvegarde.  
  
-   Si l'un des déchiffrements échoue, la restauration échoue. Vous pouvez utiliser l'option FORCE pour ignorer les erreurs, mais cette option entraîne la perte de toutes les données ne pouvant pas être déchiffrées.  
  
-   La régénération de la hiérarchie de chiffrement est une opération qui consomme beaucoup de ressources. Par conséquent, vous devez planifier cette opération au cours d'une période de faible demande.  
  
> [!CAUTION]  
>  La clé principale de service représente la racine de la hiérarchie de chiffrement [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . La clé principale de service sécurise de manière directe ou indirecte toutes les autres clés de l'arborescence. Si une clé dépendante ne peut pas être déchiffrée au cours d'une restauration forcée, les données sécurisées par cette clé sont perdues.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert l'autorisation CONTROL SERVER sur le serveur.  
  
##  <a name="SSMSProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-restore-the-service-master-key"></a>Pour restaurer la clé principale du service  
  
1.  Récupérez une copie de la clé principale du service sauvegardée, à partir d'un support de sauvegarde physique ou d'un répertoire sur le système de fichiers local.  
  
2.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
3.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
4.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Restores the service master key from a backup file.  
    RESTORE SERVICE MASTER KEY   
        FROM FILE = 'c:\temp_backups\keys\service_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  Le chemin d'accès à la clé et le mot de passe de la clé (s'il existe) seront différents de ce qui est indiqué ci-dessus. Assurez-vous que les deux sont spécifiques à votre installation de serveur et de clé.  
  
  
