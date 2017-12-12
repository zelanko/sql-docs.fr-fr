---
title: "Enregistrer le script de modification, boîte de dialogue (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
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
ms.openlocfilehash: 2566eb868dc10e76854e6f76e767b33f3413749b
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a>Boîte de dialogue Enregistrer le script de modification (Visual Database Tools)
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
  
