---
title: "Configurer les autorisations du système de fichiers pour l’accès au moteur de base de données | Microsoft Docs"
ms.custom: 
ms.date: 06/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- file system permissions
- service account [SQL Server], file system permissions
- permissions [SQL Server], file system
ms.assetid: 78bba43c-4edb-4216-84ac-d6246ae5546d
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: fc98fccf34dcc15cb255698502bf4ea4d0986249
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="configure-file-system-permissions-for-database-engine-access"></a>Configurer les autorisations du système de fichiers pour l'accès au moteur de base de données
  Cette rubrique explique comment octroyer au [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]un accès de système de fichiers à l'emplacement où sont stockés les fichiers de base de données. Le service [!INCLUDE[ssDE](../../includes/ssde-md.md)] doit disposer d'une autorisation du système de fichiers Windows pour accéder au dossier de fichiers dans lequel sont stockés les fichiers de base de données. L'autorisation sur l'emplacement par défaut est configurée lors de l'installation. Si vous placez vos fichiers de base de données à un emplacement différent, vous devrez peut-être procéder comme suit pour octroyer au [!INCLUDE[ssDE](../../includes/ssde-md.md)] une autorisation de contrôle total sur cet emplacement.  
  
 Depuis [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , les autorisations sont affectées au SID par service pour chacun de ses services. Ce système aide à fournir une isolation de service et une défense en profondeur. Le SID par service est dérivé du nom du service et est propre à chaque service. La rubrique [Configurer les comptes de service Windows et les autorisations](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md) décrit le SID par service et fournit les noms dans la section **Privilèges et droits Windows**. C'est le SID par service qui doit bénéficier d'une autorisation d'accès à l'emplacement de fichier.  
  
## <a name="to-grant-file-system-permission-to-the-per-service-sid"></a>Pour octroyer une autorisation de système de fichiers au SID par service  
  
1.  À l'aide de l'Explorateur Windows, accédez à l'emplacement du système de fichiers où sont stockés les fichiers de base de données. Cliquez avec le bouton droit sur le dossier du système de fichiers, puis sélectionnez **Propriétés**.  
  
2.  Sous l’onglet **Sécurité** , cliquez sur **Modifier**, puis sur **Ajouter**.  
  
3.  Dans la boîte de dialogue **Choisir des utilisateurs, un ordinateur, un compte de service ou des groupes** , cliquez sur **Emplacements**, en haut de la liste des emplacements, sélectionnez le nom de votre ordinateur, puis cliquez sur **OK**.  
  
4.  Dans la zone **Entrez les noms d’objets à sélectionner** , tapez le nom du SID par service répertorié dans la rubrique de la documentation en ligne [**Configurer les comptes de service Windows et les autorisations**](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md). (Pour le nom du SID par service [!INCLUDE[ssDE](../../includes/ssde-md.md)] , utilisez **NT SERVICE\MSSQLSERVER** pour une instance par défaut ou **NT SERVICE\MSSQL$InstanceName** pour une instance nommée.)  
  
5.  Cliquez sur **Vérifier les noms** pour valider l’entrée. (Si la validation échoue, cela peut indiquer que le nom était introuvable. Quand vous cliquez sur **OK**, une boîte de dialogue **Noms multiples trouvés** s’affiche. Sélectionnez maintenant le nom du SID par service, à savoir **MSSQLSERVER** ou **NT SERVICE\MSSQL$InstanceName**, puis cliquez sur **OK**.  Cliquez sur **OK** à nouveau pour revenir à la boîte de dialogue **Autorisations** .)   
6.  Dans la zone de noms **Groupe ou utilisateur**, sélectionnez le SID par service puis, dans la zone **Autorisations pour** \<nom>, cochez la case **Autoriser** pour **Contrôle total**.  
  
7. Cliquez sur **Appliquer**, puis cliquez à deux reprises sur **OK** pour quitter la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer les services du moteur de base de données](../../database-engine/configure-windows/manage-the-database-engine-services.md)   
 [Déplacer des bases de données système](../../relational-databases/databases/move-system-databases.md)   
 [Déplacer des bases de données utilisateur](../../relational-databases/databases/move-user-databases.md)  
  
  

