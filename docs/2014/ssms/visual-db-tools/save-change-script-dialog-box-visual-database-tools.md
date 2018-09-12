---
title: Enregistrer le script de modification, boîte de dialogue (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.generatechangescript
- vdtsql.chm:65544
ms.assetid: fc9d1639-5efa-44fe-a04f-4d4d0def2833
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4e44403c04ab248353149fb3c507c797b4068a73
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43814535"
---
# <a name="save-change-script-dialog-box-visual-database-tools"></a>Enregistrer le script de modification, boîte de dialogue (Visual Database Tools)
  Cette boîte de dialogue affiche le script [!INCLUDE[tsql](../../includes/tsql-md.md)] des modifications que vous avez apportées depuis le dernier enregistrement de la table. Elle permet également d'enregistrer le script dans un fichier texte à l'emplacement de votre choix.  
  
 Vous pouvez accéder à cette boîte de dialogue après avoir modifié la table sans l'enregistrer dans le Concepteur de tables. Dans le menu **Concepteur de tables** , cliquez sur **Générer un script de modification**.  
  
> [!NOTE]  
>  Les scripts de modification fournis par Visual Database Tools ne contiennent pas de gestion des erreurs. Ils supposent que les objets de la base de données n'ont pas été modifiés depuis l'ouverture de l'outil, et que les problèmes liés aux modifications ne se produiront donc pas. Avant d'exécuter un script de modification, vous devez inclure les instructions appropriées de gestion des erreurs.  
  
## <a name="options"></a>Options  
 **Générer automatiquement un script de modification à chaque enregistrement**  
 Si cette option est activée, la boîte de dialogue **Enregistrer le script de modification** s’affiche chaque fois que vous enregistrez les modifications apportées à une table.  
  
 **Oui**  
 Affiche la boîte de dialogue **Enregistrer** permettant de choisir l’emplacement du fichier texte.  
  
 **Non**  
 Annule la création du script de modification.  
  
  
