---
title: "Remplacer les paramètres de modèle | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-templates
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.templates.replaceparameters.f1
helpviewer_keywords:
- template parameters [Template Explorer]
- templates [Transact-SQL], replacing parameters
- Replace (Query) Template Parameters dialog box
- replacing template parameters
ms.assetid: 1234aa14-3464-4a3e-922a-5cfb8fb23627
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 17d36529a476493920ceb74d64069d5e77e7d10e
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="replace-template-parameters"></a>Remplacer les paramètres de modèle
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Les modèles contiennent des paramètres qui peuvent être remplacés par des valeurs spécifiques à l’implémentation chaque fois que le modèle est utilisé. Après avoir ouvert un modèle dans un éditeur de code, vous pouvez remplacer les paramètres par des valeurs pertinentes pour votre implémentation.  
  
## <a name="before-you-begin"></a>Avant de commencer  
La boîte de dialogue **Spécifier les valeurs des paramètres du modèle** est une grille avec trois colonnes. Les colonnes **Paramètre** et **Type** sont en lecture seule et ne peuvent pas être modifiées. Examinez le contenu de la colonne **Valeur** , et remplacez les valeurs par défaut par des valeurs pertinentes pour votre implémentation.  
  
Pour utiliser cette boîte de dialogue, les paramètres du script doivent être placés entre les signes « inférieur à » et « supérieur à » (`< >`) au format `<`*nom_paramètre*`,` *type_de_données*`,` *valeur_par_défaut*`>`.  
  
## <a name="replace-template-parameters"></a>Remplacer les paramètres de modèle  
Après avoir ouvert le modèle dans une fenêtre d'éditeur de code :  
  
1.  Dans le menu **Requête** , cliquez sur **Spécifier les valeurs des paramètres du modèle**.  
  
2.  Dans la boîte de dialogue **Spécifier les valeurs des paramètres du modèle** , la colonne **Valeurs** contient une valeur possible pour chaque paramètre. Acceptez la valeur ou remplacez-la par une autre valeur.  
  
3.  Cliquez sur **OK** pour fermer la boîte de dialogue **Remplacer les paramètres de modèle** et modifier le script dans l’éditeur de requête.  
  
## <a name="see-also"></a>Voir aussi  
[Template Explorer](../../ssms/template/template-explorer.md)  
[Ouvrir un modèle](../../ssms/template/open-a-template.md)  
  
