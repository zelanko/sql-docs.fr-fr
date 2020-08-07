---
title: Gestion des sauvegardes (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Oracle Backup Management
- SQL Server Backup Management
ms.assetid: a1a03ef9-b6e8-4127-bad0-eae261251472
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: b9e091db3e04eb0b82458e60f860dfb829076863
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87934720"
---
# <a name="managing-backups-oracletosql"></a>Gestion des sauvegardes (OracleToSQL)
La gestion des sauvegardes Oracle vous permet de sauvegarder et de restaurer des données de table avant ou après l’exécution d’un test. Vous pouvez également gérer le contenu de la sauvegarde avec la boîte de dialogue gérer le contenu de la sauvegarde.  
  
## <a name="oracle-backup-management"></a>Gestion des sauvegardes Oracle  
  
### <a name="backup"></a>Sauvegarde  
Pour ouvrir la boîte de dialogue sauvegarde, dans le menu testeur, pointez sur gestion des sauvegardes Oracle, puis cliquez sur sauvegarder.... Dans la boîte de dialogue de sauvegarde, vous trouverez l’arborescence de métadonnées Oracle qui affiche toutes les tables du schéma Oracle chargé. Sélectionnez une ou plusieurs tables pour effectuer une sauvegarde.  
  
Les boutons suivants sont disponibles dans la boîte de dialogue :  
  
-   Cliquez sur le bouton **vérifier l’État** pour vérifier l’état de sauvegarde de la table.  
  
-   Cliquez sur le bouton **sauvegarder** pour sauvegarder les données de la table.  
  
-   Cliquez sur le bouton **Annuler** pour fermer la boîte de dialogue.  
  
### <a name="restore"></a>Restaurer  
Pour ouvrir la boîte de dialogue Restaurer, dans le menu tester, pointez sur gestion des sauvegardes Oracle, puis cliquez sur restaurer.... Vous y trouverez une arborescence contenant les tables disponibles dans la sauvegarde. Sélectionnez une ou plusieurs tables pour restaurer ses données.  
  
Les boutons suivants sont disponibles dans la boîte de dialogue :  
  
-   Cliquez sur le bouton **vérifier l’État** pour vérifier l’état de sauvegarde de la table.  
  
-   Cliquez sur le bouton **restaurer** pour restaurer les données de sauvegarde dans la table.  
  
-   Cliquez sur le bouton **Annuler** pour fermer la boîte de dialogue.  
  
### <a name="managing-backup-contents"></a>Gestion du contenu de la sauvegarde  
Pour ouvrir gestion du contenu de la sauvegarde, dans le menu testeur, pointez sur gestion des sauvegardes Oracle, puis cliquez sur contenu de la sauvegarde.... Vous y trouverez une arborescence contenant les tables de la sauvegarde.  
  
Les boutons suivants sont disponibles dans la boîte de dialogue :  
  
-   Cliquez sur le bouton **vérifier l’État** pour vérifier l’état de sauvegarde de la table.  
  
-   Cliquez sur le bouton **supprimer** pour supprimer la table de la sauvegarde.  
  
-   Cliquez sur le bouton **Fermer** pour fermer la boîte de dialogue.  
  
## <a name="sql-server-backup-management"></a>Gestion de la sauvegarde SQL Server  
SQL Server la gestion des sauvegardes vous permet de sauvegarder et de restaurer des données de table avant ou après l’exécution d’un test. Vous pouvez également gérer le contenu de la sauvegarde avec la boîte de dialogue gérer le contenu de la sauvegarde.  
  
### <a name="backup"></a>Sauvegarde  
Pour ouvrir la boîte de dialogue sauvegarde, dans le menu tester, pointez sur SQL Server gestion de la sauvegarde, puis cliquez sur sauvegarder.... Dans la boîte de dialogue de sauvegarde, vous trouverez la SQL Server arborescence de métadonnées qui affiche toutes les tables des bases de données SQL Server chargées. Sélectionnez une ou plusieurs tables pour effectuer une sauvegarde.  
  
Les boutons suivants sont disponibles dans la boîte de dialogue :  
  
-   Cliquez sur le bouton **vérifier l’État** pour vérifier l’état de sauvegarde de la table.  
  
-   Cliquez sur le bouton **sauvegarder** pour sauvegarder les données de la table.  
  
-   Cliquez sur le bouton **Annuler** pour fermer la boîte de dialogue.  
  
### <a name="restore"></a>Restaurer  
Pour ouvrir la boîte de dialogue Restaurer, dans le menu tester, pointez sur SQL Server gestion des sauvegardes, cliquez sur restaurer.... Vous y trouverez une arborescence contenant les tables disponibles dans la sauvegarde. Sélectionnez une ou plusieurs tables pour restaurer ses données.  
  
Les boutons suivants sont disponibles dans la boîte de dialogue :  
  
-   Cliquez sur le bouton **vérifier l’État** pour vérifier l’état de sauvegarde de la table.  
  
-   Cliquez sur le bouton **restaurer** pour restaurer les données de sauvegarde dans la table.  
  
-   Cliquez sur le bouton **Annuler** pour fermer la boîte de dialogue.  
  
### <a name="managing-backup-contents"></a>Gestion du contenu de la sauvegarde  
Pour ouvrir la gestion du contenu de la sauvegarde, dans le menu tester, pointez sur SQL Server gestion de la sauvegarde, puis cliquez sur sauvegarder le contenu.... Vous y trouverez une arborescence contenant les tables de la sauvegarde.  
  
Les boutons suivants sont disponibles dans la boîte de dialogue :  
  
-   Cliquez sur le bouton **vérifier l’État** pour vérifier l’état de sauvegarde de la table.  
  
-   Cliquez sur le bouton **supprimer** pour supprimer la table de la sauvegarde.  
  
-   Cliquez sur le bouton **Fermer** pour fermer la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
[Test des objets de base de données migrés &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
