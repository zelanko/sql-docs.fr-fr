---
title: "Sauvegarder la cl&#233; principale du service | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "clé principale du service [SQL Server], exportation"
ms.assetid: f60b917c-6408-48be-b911-f93b05796904
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# Sauvegarder la cl&#233; principale du service
  Cette rubrique explique comment sauvegarder la clé principale du service dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[tsql](../../../includes/tsql-md.md)]. La clé principale du service représente la racine de la hiérarchie de chiffrement. Elle doit être sauvegardée et stockée en lieu sûr, en dehors de votre lieu de travail. La création de cette sauvegarde doit être l'une des premières actions administratives effectuées sur le serveur.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   [Pour sauvegarder la clé principale du service](#Procedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   La clé principale doit être ouverte et, par conséquent, déchiffrée avant d'être sauvegardée. Si elle est chiffrée avec la clé principale du service, la clé principale ne doit pas être explicitement ouverte ; toutefois, si la clé principale est chiffrée uniquement avec un mot de passe, elle doit être ouverte explicitement.  
  
-   Nous vous conseillons de sauvegarder la clé principale dès sa création et de stocker cette sauvegarde en lieu sûr, en dehors de votre lieu de travail.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert l'autorisation CONTROL sur la base de données.  
  
##  <a name="Procedure"></a> Utilisation de Transact-SQL  
  
#### Pour sauvegarder la clé principale du service  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connectez-vous à l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] contenant la clé principale du service à sauvegarder.  
  
2.  Choisissez un mot de passe qui servira à chiffrer la clé principale du service sur le support de sauvegarde. Ce mot de passe est sujet à des vérifications de complexité. Pour plus d'informations, consultez [Password Policy](../../../relational-databases/security/password-policy.md).  
  
3.  Procurez-vous un support de sauvegarde amovible pour stocker une copie de la clé sauvegardée.  
  
4.  Identifiez un répertoire NTFS où créer la sauvegarde de la clé. C'est à cet emplacement que vous allez créer le fichier spécifié à l'étape suivante. Le répertoire doit être protégé par des listes de contrôle d'accès très restrictives.  
  
5.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
6.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
7.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Creates a backup of the "AdventureWorks2012" master key.  
    -- Because this master key is not encrypted by the service master key, a password must be specified when it is opened.  
    USE AdventureWorks2012;  
    GO  
    BACKUP SERVICE MASTER KEY TO FILE = 'c:\temp_backups\keys\service_master_ key'   
        ENCRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    >  Le chemin d'accès à la clé et le mot de passe de la clé (s'il existe) seront différents de ce qui est indiqué ci-dessus. Vérifiez que les deux sont spécifiques à votre installation de serveur et de clé.  
  
8.  Copiez le fichier sur le support de sauvegarde et vérifiez la copie.  
  
9. Conservez la sauvegarde en lieu sûr, en dehors de votre lieu de travail.  
  
 Pour plus d’informations, consultez [OPEN MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/open-master-key-transact-sql.md) et [BACKUP MASTER KEY &#40;Transact-SQL&#41;](../../../t-sql/statements/backup-master-key-transact-sql.md).  
  
  