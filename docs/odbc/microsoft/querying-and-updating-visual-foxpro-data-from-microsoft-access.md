---
description: Interrogation et mise à jour de données Visual FoxPro à partir de Microsoft Access
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 82232cfa3c0bb32ccd87231f139e9aecf8342450
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340425"
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Interrogation et mise à jour de données Visual FoxPro à partir de Microsoft Access
Vous pouvez interroger et mettre à jour des données stockées dans une base de données Visual FoxPro à partir d’une base de données Microsoft Access à l’aide de l’option de table de liaison.  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>Pour lier une base de données Visual FoxPro à une base de données Microsoft Access  
  
1.  Ouvrez une base de données Microsoft Access.  
  
2.  Dans l’onglet tables, cliquez sur nouveau.  
  
3.  Dans la boîte de dialogue nouvelle table, sélectionnez lier la table, puis cliquez sur OK.  
  
4.  Dans la boîte de dialogue lien, sélectionnez base de données ODBC dans la liste types de fichiers.  
  
5.  Dans la boîte de dialogue sources de données SQL, sélectionnez la source de données qui se connecte aux données Visual FoxPro que vous souhaitez interroger, puis cliquez sur OK.  
  
6.  Dans la boîte de dialogue lier les tables, sélectionnez les tables que vous souhaitez interroger et mettre à jour, puis cliquez sur OK. Les tables Visual FoxPro liées sont affichées sous l’onglet tables de la base de données Microsoft Access.  
  
 Vous pouvez désormais utiliser Microsoft Access pour interroger et mettre à jour des données dans les tables Visual FoxPro liées. Les modifications que vous apportez aux données liées sont renvoyées à la source de données Visual FoxPro.  
  
 Si vous ne souhaitez pas que les modifications que vous apportez à Microsoft Access affectent les données de la source de données Visual FoxPro, consultez [importation de données Visual FoxPro dans Microsoft Access](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md).
