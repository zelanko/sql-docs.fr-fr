---
title: Interrogation et mise à jour de données Visual FoxPro à partir de Microsoft Access | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2681ecd0fe6f586954236c4fb5fddcf576b206be
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67988060"
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Interrogation et mise à jour de données Visual FoxPro à partir de Microsoft Access
Vous pouvez interroger et mettre à jour les données stockées dans une base de données Visual FoxPro à partir d’une base de données Microsoft Access à l’aide de l’option de Table de liens.  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>Pour lier une base de données Visual FoxPro à une base de données Microsoft Access  
  
1.  Ouvrez une base de données Microsoft Access.  
  
2.  Sous l’onglet Tables, cliquez sur Nouveau.  
  
3.  Dans la boîte de dialogue Nouvelle Table, sélectionnez la Table de liens, puis cliquez sur OK.  
  
4.  Dans la boîte de dialogue de lien, sélectionnez base de données ODBC dans la liste de type de fichiers.  
  
5.  Dans la boîte de dialogue Sources de données SQL, sélectionnez la source de données qui se connecte aux données Visual FoxPro que vous souhaitez interroger et cliquez sur OK.  
  
6.  Dans la boîte de dialogue Lier les Tables, sélectionnez les tables que vous souhaitez interroger et mettre à jour et cliquez sur OK. Les tables Visual FoxPro liés sont affichés dans l’onglet Tables de la base de données Microsoft Access.  
  
 Vous pouvez désormais utiliser Microsoft Access pour interroger et mettre à jour des données dans les tables Visual FoxPro liés. Modifications apportées aux données liées sont renvoyées à la source de données Visual FoxPro.  
  
 Si vous ne souhaitez pas que les modifications que vous apportez dans Microsoft Access affecte les données sur la source de données Visual FoxPro, consultez [l’importation de données dans Microsoft Access](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md).
