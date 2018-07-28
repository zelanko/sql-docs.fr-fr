---
title: Définitions de requête incohérentes, boîte de dialogue (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69639
- vdtsql.chm:69640
- vdt.dlgbox.querydefinitionsdiffer
ms.assetid: 90383473-2922-40e5-9682-3850849aa856
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d23ec7b92c696f337d3a1c7bb9b44905f57f9c8b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204589"
---
# <a name="query-definitions-differ-dialog-box-visual-database-tools"></a>Définitions de requête incohérentes, boîte de dialogue (Visual Database Tools)
  Cette boîte de dialogue vous informe que votre requête ne peut pas être représentée graphiquement dans les volets Schéma et Critères, et qu'elle peut être modifiée seulement dans le volet SQL.  
  
 Elle peut apparaître quand vous entrez ou modifiez une instruction SQL dans le volet SQL ; vous passez alors à un autre volet, vérifiez la requête ou tentez d’exécuter la requête, et l’une des conditions suivantes s’applique :  
  
-   L'instruction SQL est incomplète ou contient une ou plusieurs erreurs de syntaxe.  
  
-   L'instruction SQL est valide mais n'est pas prise en charge dans les volets graphiques (par exemple, une requête Union).  
  
-   L'instruction SQL est valide mais contient une syntaxe spécifique à la connexion de données que vous utilisez.  
  
> [!TIP]  
>  Vous pouvez vérifier si une instruction est valide à l’aide du bouton **Vérifier l’instruction SQL** situé dans la barre d’outils **Requête** .  
  
 La boîte de dialogue affiche un message expliquant la raison pour laquelle l'instruction SQL ne peut pas être représentée, puis vous demande comment vous souhaitez poursuivre.  
  
> [!NOTE]  
>  La boîte de dialogue **Définitions de requête incohérentes** n’apparaît pas si vous avez masqué les volets Schéma et Critères.  
  
## <a name="options"></a>Options  
 **Bouton Ignorer**  
 Choisissez ce bouton pour spécifier que vous acceptez l'instruction SQL, pour la modifier ultérieurement ou pour l'exécuter. Si vous acceptez l'instruction, les volets Schéma et Critères apparaissent estompés pour indiquer qu'ils ne représentent pas l'instruction dans le volet SQL.  
  
 **Bouton Annuler**  
 Choisissez ce bouton pour annuler les modifications que vous avez apportées au volet SQL.  
  
> [!NOTE]  
>  Si l'instruction est correcte, mais si sa représentation graphique n'est pas prise en charge par le Concepteur de requêtes et de vues, vous pouvez l'exécuter même si elle ne peut pas être représentée dans les volets Schéma et Critères. Par exemple, si vous entrez une requête Union, l'instruction peut être exécutée mais pas représentée dans les autres volets.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils du concepteur de requêtes et de vues &#40;Visual Database Tools&#41;](visual-database-tools.md)  
  
  