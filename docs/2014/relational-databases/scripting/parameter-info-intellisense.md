---
title: Information sur les paramètres (IntelliSense) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Parameter Info option [IntelliSense]
- stored function parameter completion [Intellisense]
- language references [SQL Server]
- IntelliSense [SQL Server], Parameter Info option
ms.assetid: 56c2aac9-c65c-4679-b62c-d9f689876dde
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c79538695c6770e0d3c9025165137ca2823011f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37329279"
---
# <a name="parameter-info-intellisense"></a>Information sur les paramètres (IntelliSense)
  L’option [!INCLUDE[msCoName](../../includes/msconame-md.md)] Informations sur les paramètres **de** IntelliSense ouvre une liste de paramètres qui fournit des informations sur le nombre, le nom et le type des paramètres requis par une fonction ou une procédure stockée. Le paramètre en gras indique le prochain paramètre requis lorsque vous tapez une fonction ou une procédure stockée.  
  
 La liste des paramètres est également affichée pour les fonctions imbriquées. Si vous tapez une fonction comme paramètre d'une autre fonction, la liste affiche dans un premier temps les paramètres de la fonction interne. Dans un second temps, la liste affiche les paramètres de la fonction externe.  
  
#### <a name="to-view-parameter-info-for-functions-or-stored-procedures"></a>Pour afficher l'option Informations sur les paramètres pour les fonctions ou les procédures stockées  
  
1.  À la suite du nom de la fonction, tapez une parenthèse ouvrante comme vous le feriez normalement pour ouvrir une liste de paramètres. Après avoir tapé le nom d'une procédure stockée, tapez un espace comme vous le feriez normalement pour obtenir des informations à propos des paramètres d'une procédure.  
  
     IntelliSense affiche la déclaration complète de la fonction ou les paramètres de la procédure stockée dans une fenêtre indépendante, juste sous le point d'insertion. Le premier paramètre de la liste est affiché en gras.  
  
2.  À mesure que vous tapez les paramètres, le paramètre suivant à entrer vous est indiqué en gras.  
  
3.  Appuyez sur ÉCHAP pour fermer la liste ou continuez à taper la fonction jusqu'à la fin.  
  
     Dans le cas d'une fonction, si vous tapez la parenthèse fermante, vous fermez également la liste des paramètres.  
  
#### <a name="to-manually-start-parameter-info"></a>Pour démarrer manuellement l'option Informations sur les paramètres  
  
1.  Dans le menu **Edition** , sélectionnez **IntelliSense** , puis **Informations sur les paramètres**.  
  
2.  Utilisez le raccourci clavier CTRL+MAJ+ESPACE.  
  
 Pour plus d’informations, consultez [Configurer IntelliSense &#40;SQL Server Management Studio&#41;](configure-intellisense-sql-server-management-studio.md).  
  
> [!NOTE]  
>  L’option **Informations sur les paramètres** est uniquement disponible pour l’éditeur de requête [!INCLUDE[ssDE](../../includes/ssde-md.md)] et l’Éditeur de requête XML.  
  
  
