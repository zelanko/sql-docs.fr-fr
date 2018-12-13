---
title: Rapprocher un schéma de base de données et une base de données modifiée (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- updating diagram to match database
- reconciling database diagrams
- diagrams [SQL Server], reconciling changes
- updating database to match diagram
- database diagrams [SQL Server], reconciling changes
ms.assetid: eda8dea2-eedd-43a7-85aa-92bd97783b5f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0c93f7c1d22b5f2d41b196eddd20ba5a4ff097cf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141689"
---
# <a name="reconcile-a-database-diagram-with-a-modified-database-visual-database-tools"></a>Rapprocher un diagramme de base de données et une base de données modifiée (Visual Database Tools)
  Vous enregistrez votre diagramme de base de données lorsque vous êtes prêt à mettre à jour la base de données par rapport à ce diagramme. Toutefois, si d'autres utilisateurs ont mis à jour la base de données depuis l'ouverture de votre schéma, leurs modifications risquent d'avoir une incidence sur le schéma et vice versa.  
  
 L'enregistrement de votre schéma provoquera un rapprochement entre votre base de données et votre schéma en écrasant les autres modifications des utilisateurs, de telle sorte que votre base de données corresponde à votre schéma.  
  
### <a name="to-update-a-database-to-match-your-diagram"></a>Pour mettre à jour une base de données afin qu'elle corresponde à votre schéma  
  
1.  Enregistrez votre diagramme de base de données.  
  
     Si vous n’avez pas encore enregistré votre diagramme, tapez le nom que vous voulez lui attribuer dans la boîte de dialogue **Enregistrer un nouveau diagramme de base de données** et cliquez sur **OK**.  
  
2.  La boîte de dialogue **Enregistrer** affiche la liste des tables qui seront affectées quand vous enregistrerez votre schéma. Choisissez **Oui** pour continuer.  
  
3.  La boîte de dialogue **Modifications détectées dans la base de données** affiche la liste des objets qui ont changé et qui seront modifiés de façon à correspondre à votre schéma. Choisissez **Oui** pour enregistrer le schéma et accepter la liste des changements.  
  
    > [!NOTE]  
    >  Si votre schéma contient des tables et des colonnes qui ont été supprimées de la base de données, seules leurs définitions sont recréées dans la base de données lorsque vous enregistrez votre schéma. Ce processus ne restaure pas les données qui existaient dans ces objets avant leur suppression.  
  
### <a name="to-update-your-diagram-to-match-a-modified-database"></a>Pour mettre à jour votre schéma afin qu'il corresponde à une base de données modifiée  
  
1.  Fermez votre schéma sans enregistrer les modifications.  
  
2.  Cliquez avec le bouton droit sur le schéma dans l'Explorateur d'objets.  
  
3.  Dans le menu contextuel, cliquez sur **Actualiser**.  
  
4.  Rouvrez le schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [Utiliser des schémas de base de données &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  
