---
title: "Enregistrer le script de modification, boîte de dialogue (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 10018ea2f1949da54c7dfc084ee204ad5619c6ca
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a>Enregistrer le script de modification, boîte de dialogue (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Cette boîte de dialogue affiche le script [!INCLUDE[tsql](../../includes/tsql_md.md)] des changements que vous avez apportés depuis le dernier enregistrement de la table. Elle permet également d'enregistrer le script dans un fichier texte à l'emplacement de votre choix.  
  
Vous pouvez accéder à cette boîte de dialogue après avoir modifié la table sans l'enregistrer dans le Concepteur de tables. Dans le menu **Concepteur de tables** , cliquez sur **Générer un script de modification**.  
  
> [!NOTE]  
> Les scripts de modification fournis par Visual Database Tools ne contiennent pas de gestion des erreurs. Ils supposent que les objets de la base de données n'ont pas été modifiés depuis l'ouverture de l'outil, et que les problèmes liés aux modifications ne se produiront donc pas. Avant d'exécuter un script de modification, vous devez inclure les instructions appropriées de gestion des erreurs.  
  
## <a name="options"></a>Options  
**Générer automatiquement un script de modification à chaque enregistrement**  
Si cette option est activée, la boîte de dialogue **Enregistrer le script de modification** s’affiche chaque fois que vous enregistrez les modifications apportées à une table.  
  
**Oui**  
Affiche la boîte de dialogue **Enregistrer** permettant de choisir l’emplacement du fichier texte.  
  
**Non**  
Annule la création du script de modification.  
  
