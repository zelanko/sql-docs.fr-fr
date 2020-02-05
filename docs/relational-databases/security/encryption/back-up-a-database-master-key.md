---
title: Sauvegarder une clé primaire de base de données | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], exporting
ms.assetid: 7ad9a0a0-6e4f-4f7b-8801-8c1b9d49c4d8
author: jaszymas
ms.author: jaszymas
ms.openlocfilehash: 55db3923f26acaad667e444afb13ae0d86bcc59e
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "74957501"
---
# <a name="back-up-a-database-master-key"></a>Sauvegarder une clé primaire de base de données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette rubrique explique comment sauvegarder une clé principale de base de données dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. La clé principale d'une base de données permet de chiffrer d'autres clés et certificats à l'intérieur d'une base de données. Si celle-ci est supprimée ou endommagée, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] risque de ne pas pouvoir déchiffrer ces clés, et les données chiffrées qui les utilisent seront perdues. C'est pourquoi vous devez sauvegarder la clé principale de la base de données et stocker la sauvegarde dans un emplacement sécurisé, en dehors de votre lieu de travail.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="limitations-and-restrictions"></a>Limitations et restrictions  
  
- La clé principale doit être ouverte et, par conséquent, déchiffrée avant d'être sauvegardée. Si elle est chiffrée avec la clé principale de service, il n'est pas nécessaire que la clé principale soit ouverte explicitement. En revanche, si la clé principale est chiffrée seulement à l'aide d'un mot de passe, elle doit être ouverte explicitement.  
  
- Nous vous conseillons de sauvegarder la clé principale dès sa création et de stocker cette sauvegarde en lieu sûr, en dehors de votre lieu de travail.  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations
Requiert l'autorisation CONTROL sur la base de données.  
  
## <a name="using-sql-server-management-studio-with-transact-sql"></a>Utilisation de SQL Server Management Studio avec Transact-SQL  
  
### <a name="to-back-up-the-database-master-key"></a>Pour sauvegarder la clé principale de base de données  
  
1. Dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connectez-vous à l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] contenant la clé principale de base de données à sauvegarder.  
  
2. Choisissez un mot de passe qui servira à chiffrer la clé principale de base de données sur le support de sauvegarde. Ce mot de passe est sujet à des vérifications de complexité.  
  
3. Procurez-vous un support de sauvegarde amovible pour stocker une copie de la clé sauvegardée.  
  
4. Identifiez un répertoire NTFS où créer la sauvegarde de la clé. C'est à cet emplacement que vous allez créer le fichier spécifié à l'étape suivante. Le répertoire doit être protégé par des listes de contrôle d'accès très restrictives.  
  
5. Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
6. Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
7. Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```sql
    -- Creates a backup of the "AdventureWorks2012" master key. Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;   
    GO  
    OPEN MASTER KEY DECRYPTION BY PASSWORD = 'sfj5300osdVdgwdfkli7';   
  
    BACKUP MASTER KEY TO FILE = 'c:\temp\exportedmasterkey'   
        ENCRYPTION BY PASSWORD = 'sd092735kjn$&adsg';   
    GO  
    ```  
  
    > [!NOTE]  
    > Le chemin d'accès à la clé et le mot de passe de la clé (s'il existe) seront différents de ce qui est indiqué ci-dessus. Assurez-vous que les deux sont spécifiques à votre installation de serveur et de clé.  
  
8. Copiez le fichier sur le support de sauvegarde et vérifiez la copie.  
  
9. Conservez la sauvegarde en lieu sûr, en dehors de votre lieu de travail.  
  
 Pour plus d’informations, consultez [OPEN MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/open-master-key-transact-sql.md) et [BACKUP MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/backup-master-key-transact-sql.md).  
