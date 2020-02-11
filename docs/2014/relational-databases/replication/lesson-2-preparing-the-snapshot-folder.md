---
title: 'Leçon 2 : Préparation du dossier d’instantanés | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: f286cde9-c0d0-43ef-b7ba-53c3cbb8906c
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 5ec45b0a29f9f4c8fb1e6a9b683e47797f194885
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721020"
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
  
7.  Dans la boîte de dialogue **Autorisations** , cliquez sur **Ajouter**. Dans la zone de texte **Sélectionner les utilisateurs, les ordinateurs, le compte de service ou les groupes** , tapez le nom du compte agent d’instantané créé au \<cours de la leçon 1, comme _Machine_Name>_ **\ repl_snapshot**, où \< *Machine_Name>* est le nom du serveur de publication. Cliquez sur **Vérifier les noms**, puis sur **OK**.  
  
8.  Répétez l’étape précédente pour ajouter des autorisations pour le agent de distribution \<, comme _Machine_Name>_ **\ repl_distribution**, et pour le \< _agent de fusion en tant que Machine_Name>_ **\ repl_merge**.  
  
9. Vérifiez que les autorisations suivantes sont accordées :  
  
    -   repl_snapshot - Contrôle total  
  
    -   repl_distribution - Lecture  
  
    -   repl_merge - Lecture  
  
10. Cliquez sur **OK** pour fermer la boîte de dialogue **Propriétés de repldata** et créer le partage repldata.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez configuré avec succès le partage du dossier d'instantanés. Ensuite, vous allez configurer la distribution. Consultez [Leçon 3 : Configuration de la distribution](lesson-3-configuring-distribution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser le dossier d’instantanés](security/secure-the-snapshot-folder.md)  
  
  
