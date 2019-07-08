---
title: Sauvegarder la clé principale du service | Microsoft Docs
ms.custom: ''
ms.date: 01/02/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], exporting
ms.assetid: f60b917c-6408-48be-b911-f93b05796904
author: aliceku
ms.author: aliceku
manager: craigg
ms.openlocfilehash: 6e0d1da7b4910e4d3d6268be23c36fb69b16dc62
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67583668"
---
# <a name="back-up-the-service-master-key"></a>Sauvegarder la clé principale du service
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cet article explique comment sauvegarder la clé principale du service dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. La clé principale du service représente la racine de la hiérarchie de chiffrement. Elle doit être sauvegardée et stockée en lieu sûr, en dehors de votre lieu de travail. La création de cette sauvegarde doit être l'une des premières actions administratives effectuées sur le serveur.  

## <a name="before-you-begin"></a>Avant de commencer  
  
### <a name="limitations-and-restrictions"></a>Limitations et restrictions  

- La clé principale doit être ouverte et, par conséquent, déchiffrée avant d'être sauvegardée. Si elle est chiffrée avec la clé principale du service, la clé principale ne doit pas être explicitement ouverte ; toutefois, si la clé principale est chiffrée uniquement avec un mot de passe, elle doit être ouverte explicitement.  
  
- Nous vous conseillons de sauvegarder la clé principale dès sa création et de stocker cette sauvegarde en lieu sûr, en dehors de votre lieu de travail.  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations
Requiert l'autorisation CONTROL sur la base de données.  
  
## <a name="using-transact-sql"></a>Utilisation de Transact-SQL  
  
### <a name="to-back-up-the-service-master-key"></a>Pour sauvegarder la clé principale du service
  
1. Dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connectez-vous à l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] contenant la clé principale du service à sauvegarder.  
  
2. Choisissez un mot de passe qui servira à chiffrer la clé principale du service sur le support de sauvegarde. Ce mot de passe est sujet à des vérifications de complexité. Pour plus d'informations, consultez [Password Policy](../../../relational-databases/security/password-policy.md).  
  
3. Procurez-vous un support de sauvegarde amovible pour stocker une copie de la clé sauvegardée.  
  
4. Identifiez un répertoire NTFS où créer la sauvegarde de la clé. Ce répertoire est l’emplacement où vous allez créer le fichier spécifié à l’étape suivante. Le répertoire doit être protégé par des listes de contrôle d'accès très restrictives.  
  
5. Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
6. Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
7. Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```sql
    -- Creates a backup of the service master key.
    USE master;
    GO
    BACKUP SERVICE MASTER KEY TO FILE = 'c:\temp_backups\keys\service_master_ key'
        ENCRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';
    GO
    ```  
  
    > [!NOTE]  
    > Le chemin d'accès à la clé et le mot de passe de la clé (s'il existe) seront différents de ce qui est indiqué ci-dessus. Vérifiez que les deux sont spécifiques à votre installation de serveur et de clé.
  
8. Copiez le fichier sur le support de sauvegarde et vérifiez la copie.  
  
9. Conservez la sauvegarde en lieu sûr, en dehors de votre lieu de travail.  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

 Pour plus d’informations, consultez [OPEN MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/open-master-key-transact-sql.md) et [BACKUP MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/backup-master-key-transact-sql.md).  
