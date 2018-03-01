---
title: "Leçon 2 : Préparation du dossier d’instantanés | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f286cde9-c0d0-43ef-b7ba-53c3cbb8906c
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 969aca3b97e12f5a179c9f2fb4c748d93d89c760
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="lesson-2-preparing-the-snapshot-folder"></a>Leçon 2 : Préparation du dossier d'instantanés
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Dans cette leçon, vous allez apprendre à configurer le dossier d'instantanés utilisé pour créer et stocker l'instantané des publications.  
  
### <a name="to-create-a-share-for-the-snapshot-folder-and-assign-permissions"></a>Pour créer un partage pour le dossier d'instantanés et attribuer les autorisations  
  
1.  Dans l'Explorateur Windows, accédez au dossier des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L'emplacement par défaut est : C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data.  
  
2.  Créez un dossier nommé **repldata**.  
  
3.  Cliquez avec le bouton droit sur ce dossier, puis sélectionnez **Propriétés**.  
  
4.  Sous l’onglet **Partage** de la boîte de dialogue **Propriétés de repldata** , cliquez sur **Partager**.  
  
5.  Dans la boîte de dialogue **Partage de fichiers** , cliquez sur **Partager**, puis sur **Terminé**.  
  
6.  Sur l'onglet **Sécurité** , cliquez sur **Modifier**.  
  
7.  Dans la boîte de dialogue **Autorisations** , cliquez sur **Ajouter**. Dans la zone de texte **Sélectionnez Utilisateurs, Ordinateurs, Compte de service ou Groupes**, tapez le nom du compte d’Agent d’instantané créé à la leçon 1, sous la forme \<*nom_ordinateur>***\repl_snapshot**, où \<*nom_ordinateur>* est le nom du serveur de publication. Cliquez sur **Vérifier les noms**, puis sur **OK**.  
  
8.  Répétez l’étape précédente pour ajouter des autorisations pour l’Agent de distribution, sous la forme \<*nom_ordinateur>***\repl_distribution**, et pour l’Agent de fusion, sous la forme \<*nom_ordinateur>***\repl_merge**.  
  
9. Vérifiez que les autorisations suivantes sont accordées :  
  
    -   repl_snapshot - Contrôle total  
  
    -   repl_distribution - Lecture  
  
    -   repl_merge - Lecture  
  
10. Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés de repldata** et créer le partage repldata.  
  
## <a name="next-steps"></a>Next Steps  
Vous avez configuré avec succès le partage du dossier d'instantanés. Ensuite, vous allez configurer la distribution. Consultez [Leçon 3 : Configuration de la distribution](../../relational-databases/replication/lesson-3-configuring-distribution.md).  
  
## <a name="see-also"></a> Voir aussi  
[Sécuriser le dossier d'instantané](../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
  
  
