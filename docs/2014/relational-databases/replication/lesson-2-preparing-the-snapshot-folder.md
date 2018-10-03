---
title: 'Leçon 2 : Préparation du dossier d’instantanés | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f286cde9-c0d0-43ef-b7ba-53c3cbb8906c
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 9ee7028a14cebadd6d49fac1a081e8db78ea7990
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48157029"
---
# <a name="lesson-2-preparing-the-snapshot-folder"></a>Leçon 2 : Préparation du dossier d'instantanés
  Dans cette leçon, vous allez apprendre à configurer le dossier d'instantanés utilisé pour créer et stocker l'instantané des publications.  
  
### <a name="to-create-a-share-for-the-snapshot-folder-and-assign-permissions"></a>Pour créer un partage pour le dossier d'instantanés et attribuer les autorisations  
  
1.  Dans l'Explorateur Windows, accédez au dossier des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . L'emplacement par défaut est : C:\Program Files\Microsoft SQL Server\MSSQL.X\MSSQL\Data.  
  
2.  Créez un dossier nommé **repldata**.  
  
3.  Cliquez avec le bouton droit sur ce dossier, puis sélectionnez **Propriétés**.  
  
4.  Sous l’onglet **Partage** de la boîte de dialogue **Propriétés de repldata** , cliquez sur **Partager**.  
  
5.  Dans la boîte de dialogue **Partage de fichiers** , cliquez sur **Partager**, puis sur **Terminé**.  
  
6.  Sur l'onglet **Sécurité** , cliquez sur **Modifier**.  
  
7.  Dans la boîte de dialogue **Autorisations** , cliquez sur **Ajouter**. Dans la zone de texte **Sélectionnez Utilisateurs, Ordinateurs, Compte de service ou Groupes**, tapez le nom du compte d’Agent d’instantané créé à la leçon 1, sous la forme \<*nom_ordinateur>***\repl_snapshot**, où \<* nom_ordinateur>* est le nom du serveur de publication. Cliquez sur **Vérifier les noms**, puis sur **OK**.  
  
8.  Répétez l’étape précédente pour ajouter des autorisations pour l’Agent de distribution, sous la forme \<*nom_ordinateur>***\repl_distribution**, et pour l’Agent de fusion, sous la forme \<* nom_ordinateur>***\repl_merge**.  
  
9. Vérifiez que les autorisations suivantes sont accordées :  
  
    -   repl_snapshot - Contrôle total  
  
    -   repl_distribution - Lecture  
  
    -   repl_merge - Lecture  
  
10. Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés de repldata** et créer le partage repldata.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez configuré avec succès le partage du dossier d'instantanés. Ensuite, vous allez configurer la distribution. Consultez [Leçon 3 : Configuration de la distribution](lesson-3-configuring-distribution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser le dossier d'instantané](security/secure-the-snapshot-folder.md)  
  
  
