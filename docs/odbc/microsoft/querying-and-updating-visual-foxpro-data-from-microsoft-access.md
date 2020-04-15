---
title: Requête et mise à jour des données visuelles FoxPro de Microsoft Access (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- querying Visual FoxPro data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], querying and updating
- updating Visual FoxPro data [ODBC]
ms.assetid: 2d314e78-9edf-44b2-bd8b-96784236bcbe
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f11b49ed099ba29d0e7e013af99a8ad96ca6825c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292869"
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Interrogation et mise à jour de données Visual FoxPro à partir de Microsoft Access
Vous pouvez interroger et mettre à jour les données stockées dans une base de données Visual FoxPro à partir d’une base de données Microsoft Access en utilisant l’option Link Table.  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>Pour lier une base de données Visual FoxPro à une base de données Microsoft Access  
  
1.  Ouvrez une base de données Microsoft Access.  
  
2.  De l’onglet Tables, cliquez sur Nouveau.  
  
3.  Dans la boîte de dialogue New Table, sélectionnez Link Table et cliquez sur OK.  
  
4.  Dans la boîte Link Dialog, sélectionnez la base de données ODBC dans les fichiers de la liste de type.  
  
5.  Dans la boîte de dialogue SQL Data Sources, sélectionnez la source de données qui se connecte aux données Visual FoxPro que vous souhaitez interroger et cliquer sur OK.  
  
6.  Dans la boîte de dialogue Link Tables, sélectionnez les tables que vous souhaitez interroger et mettre à jour et cliquez sur OK. Les tables Visual FoxPro liées sont affichées dans l’onglet Tables de la base de données Microsoft Access.  
  
 Vous pouvez maintenant utiliser Microsoft Access pour interroger et mettre à jour les données dans les tables Visual FoxPro liées. Les modifications que vous effectuez vers des données liées sont renvoyées à la source de données Visual FoxPro.  
  
 Si vous ne voulez pas que les modifications que vous modifiez dans Microsoft Access affectent les données de la source de données Visual FoxPro, voir [Importing Visual FoxPro Data dans Microsoft Access](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md).
