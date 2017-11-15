---
title: "Enregistrer des tables sélectionnées dans un schéma (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: saving tables
ms.assetid: 86943b49-48f3-432c-8021-928c13edfbcf
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a6ac219c016292fc134aa1a1053812365d2f754d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="save-selected-tables-on-a-diagram-visual-database-tools"></a>Enregistrer des tables sélectionnées dans un schéma (Visual Database Tools)
Si vous ne souhaitez pas enregistrer toutes les modifications que vous avez apportées à un schéma de base de données, vous pouvez enregistrer une table ou un groupe de tables spécifique.  
  
### <a name="to-save-selected-tables"></a>Pour enregistrer les tables sélectionnées  
  
1.  Dans votre schéma de base de données, sélectionnez les tables que vous voulez enregistrer.  
  
2.  Dans le menu **Fichier** , cliquez sur **Enregistrer la sélection**.  
  
3.  La boîte de dialogue **Enregistrer** affiche la liste des tables qui seront mises à jour dans la base de données quand vous enregistrerez votre sélection.  
  
    Choisissez **Enregistrer comme fichier texte** si vous voulez enregistrer la liste des tables dans un fichier texte à l’intérieur du répertoire du projet avant de continuer.  
  
4.  Dans la boîte de dialogue **Enregistrer** , vérifiez la liste des tables et choisissez **Oui** pour enregistrer ces tables.  
  
    > [!NOTE]  
    > La liste des tables peut contenir d'autres tables en plus de celles que vous avez sélectionnées. Par exemple, si vous changez le type de données d'une colonne qui participe à une relation avec une autre table, les deux tables seront incluses dans cette liste.  
  
## <a name="see-also"></a>Voir aussi  
[Utiliser des schémas de base de données (Visual Database Tools)](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
  
