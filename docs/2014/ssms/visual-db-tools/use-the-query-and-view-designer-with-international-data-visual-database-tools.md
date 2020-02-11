---
title: Utiliser le concepteur de requêtes et de vues avec des données internationales (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Visual Database Tools [SQL Server], international data
- queries [SQL Server], international data
- languages [SQL Server], Query and View Designer
- international considerations [SQL Server], Query and View Designer
- Criteria pane
- View Designer, international data
- Query Designer [SQL Server], international data
- localized information in Query and View Designer [SQL Server]
- global considerations [SQL Server], Query and View Designer
- SQL pane [Visual Database Tools]
- multiple language support [SQL Server], Query and View Designer
ms.assetid: 4b51c56f-f902-4e72-b919-e36127369b63
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 673ad13ff5688fb17eaa4b975644256f072a3aef
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63204620"
---
# <a name="use-the-query-and-view-designer-with-international-data-visual-database-tools"></a>Utiliser le Concepteur de requêtes et de vues avec des données internationales (Visual Database Tools)
  Vous pouvez utiliser le [Concepteur de requêtes et de vues](visual-database-tools.md) avec des données dans n’importe quelle langue et dans n’importe quelle version du système d’exploitation Windows. Vous trouverez ci-dessous les quelques différences que vous pourrez rencontrer ainsi que des informations sur la gestion des données dans des applications internationales.  
  
## <a name="localized-information-in-the-criteria-and-sql-panes"></a>Informations localisées dans les volets Critères et SQL  
 Si vous utilisez le volet Critères pour créer votre requête, vous pouvez entrer vos informations dans le format prévu sur votre ordinateur, dans les Paramètres régionaux de Windows. Par exemple, si vous recherchez des données, vous pouvez entrer les données dans les colonnes Critères en utilisant le format auquel vous êtes habitué, avec les quelques exceptions suivantes :  
  
-   Les formats de données longs ne sont pas pris en charge.  
  
-   N'utilisez pas de symbole monétaire dans le volet Critères.  
  
-   Les symboles monétaires ne s'affichent pas dans le volet Résultats.  
  
    > [!NOTE]  
    >  Dans le volet Résultats, vous pouvez réellement entrer le symbole monétaire qui correspond aux Paramètres régionaux de Windows pour votre ordinateur, mais ce symbole sera supprimé et ne s'affichera pas dans le volet Résultats.  
  
-   L'opérateur moins unaire apparaît toujours à gauche (par exemple, -1) quelles que soient les options choisies dans les Paramètres régionaux.  
  
 Par contre, les données et les mots clés du volet SQL doivent toujours être au format ANSI (États-Unis). Par exemple, lorsque le Concepteur de requêtes et de vues génère une requête, il insère tous les mots clés SQL, tels que SELECT et FROM, au format ANSI. Si vous ajoutez des éléments à l'instruction dans le volet SQL, veillez à ce qu'ils respectent le format ANSI.  
  
 Lorsque vous entrez des données au format régional dans le volet Critères, le Concepteur de requêtes et de vues les convertit automatiquement au format ANSI dans le volet SQL. Par exemple, si le Français (standard) a été choisi dans vos Paramètres régionaux, vous pouvez entrer sur le volet Critères une date au format « 31/12/96 ». Toutefois, la date apparaîtra dans le volet SQL au format de date et heure ANSI `{ ts '1996-12-31 00:00:00' }.` . Si vous entrez directement des données dans le volet SQL, vous devez les entrer au format ANSI.  
  
## <a name="sort-order"></a>Ordre de tri  
 L'ordre de tri des données d'une requête est déterminé par la base de données. Les options définies dans la boîte de dialogue Paramètres régionaux de Windows n'affectent pas l'ordre de tri des requêtes. Cependant, à l'intérieur d'une requête, vous pouvez demander un tri selon un ordre particulier.  
  
## <a name="using-double-byte-characters"></a>Utilisation de caractères codés sur deux octets  
 Les caractères codés sur deux octets, ou caractères DBCS (Double Byte Character Set), peuvent être utilisés pour des noms d'objets de bases de données tels que des noms de tables et de vues ou d'alias. Vous pouvez également les utiliser pour des noms de paramètres et des marqueurs de paramètres. Cependant, vous ne pouvez pas les utiliser dans des éléments du langage SQL tels que des noms de fonctions ou des mots clés SQL.  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures relatives à la conception de requêtes et de vues &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
  
