---
title: Interrogation et la mise à jour de données Visual FoxPro à partir de Microsoft Access | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- querying Visual FoxPro data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], querying and updating
- updating Visual FoxPro data [ODBC]
ms.assetid: 2d314e78-9edf-44b2-bd8b-96784236bcbe
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6eefdf130a261945a17c9ec557235b65ab7133fb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Interrogation et la mise à jour de données Visual FoxPro à partir de Microsoft Access
Vous pouvez interroger et mettre à jour les données stockées dans une base de données Visual FoxPro à partir d’une base de données Microsoft Access à l’aide de l’option de Table de liens.  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>Pour lier une base de données Visual FoxPro à une base de données Microsoft Access  
  
1.  Ouvrez une base de données Microsoft Access.  
  
2.  Sous l’onglet Tables, cliquez sur Nouveau.  
  
3.  Dans la boîte de dialogue Nouvelle Table, sélectionnez la Table de liens et cliquez sur OK.  
  
4.  Dans la boîte de dialogue de lien, sélectionnez base de données ODBC dans la liste de type de fichiers.  
  
5.  Dans la boîte de dialogue de Sources de données SQL, sélectionnez la source de données qui se connecte aux données Visual FoxPro que vous souhaitez interroger et cliquez sur OK.  
  
6.  Dans la boîte de dialogue Lier les Tables, sélectionnez les tables que vous voulez interroger et mettre à jour, cliquez sur OK. Les tables Visual FoxPro liées sont affichés dans l’onglet Tables de la base de données Microsoft Access.  
  
 Vous pouvez désormais utiliser Microsoft Access pour interroger et mettre à jour des données dans les tables Visual FoxPro liés. Modifications apportées aux données liées sont renvoyées à la source de données Visual FoxPro.  
  
 Si vous ne souhaitez pas que les modifications que vous apportez dans Microsoft Access pour affecter les données sur la source de données Visual FoxPro, consultez [l’importation de données dans Microsoft Access](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md).
