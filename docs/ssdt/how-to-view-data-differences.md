---
title: 'Guide pratique : Voir les différences entre les données | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql.data.tools.datacompare.f1
ms.assetid: f88d3350-2eaf-44cc-96a8-84008b6cd071
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a7025a59d6db451bb008bca72909bed16b1803da
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094127"
---
# <a name="how-to-view-data-differences"></a>Guide pratique : Voir les différences entre les données
Après avoir comparé les données de deux bases de données, vous pourrez voir chacun des *objets de base de données* que vous avez comparés ainsi que son état. Vous pouvez également afficher les résultats des enregistrements dans chaque objet, regroupés par état.  
  
Après avoir affiché les différences, vous pourrez mettre à jour la *cible* de sorte qu’elle corresponde à la *source* pour une partie ou l’ensemble des objets ou des enregistrements qui sont différents, manquants ou nouveaux.  
  
### <a name="to-view-data-differences"></a>Pour afficher les différences entre les données  
  
1.  Comparez les données dans une source et une cible.  
  
2.  (Facultatif) Effectuez une des actions suivantes ou les deux :  
  
    -   Par défaut, les résultats pour tous les objets apparaissent, indépendamment de leur état. Pour afficher uniquement les objets qui ont un état particulier, cliquez sur l’une des options de la liste **Filtrer**.  
  
    -   Pour afficher les résultats des enregistrements d’un objet en particulier, cliquez sur cet objet dans le volet de résultats principal, puis sur un onglet du volet Vue des enregistrements. Chaque onglet affiche tous les enregistrements de cet objet qui ont un état particulier : différent, uniquement dans la source, uniquement dans la cible et en double. Les données s'affichent par enregistrement et colonne.  
  
## <a name="see-also"></a> Voir aussi  
[Guide pratique : Utiliser Comparer les schémas pour comparer différentes définitions de base de données](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)  
  
