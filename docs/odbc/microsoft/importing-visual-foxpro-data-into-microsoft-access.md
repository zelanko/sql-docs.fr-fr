---
description: Importation de données Visual FoxPro dans Microsoft Access
title: Importation de données Visual FoxPro dans Microsoft Access | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], importing
ms.assetid: a3591295-0a76-4e3c-b4fa-8bd4f1cde705
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 38440ca61b8af951f201978013d30529b75a452b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449531"
---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>Importation de données Visual FoxPro dans Microsoft Access
Vous pouvez importer des données stockées dans une base de données Visual FoxPro dans une base de données Microsoft Access à l’aide de l’option d’importation.  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>Pour importer des données Visual FoxPro dans une base de données Microsoft Access  
  
1.  Ouvrez une base de données Microsoft Access.  
  
2.  Dans le menu fichier, choisissez données externes puis importer.  
  
3.  Dans la boîte de dialogue Importer, sélectionnez bases de données ODBC dans la liste types de fichiers.  
  
4.  Dans la boîte de dialogue sources de données SQL, sélectionnez la source de données Visual FoxPro qui se connecte aux données FoxPro que vous souhaitez interroger, puis cliquez sur OK.  
  
5.  Dans la boîte de dialogue Importer des objets, sélectionnez une ou plusieurs tables que vous souhaitez importer, puis cliquez sur OK. Les noms des tables Visual FoxPro que vous avez importées s’affichent sous l’onglet tables de la base de données Microsoft Access.  
  
 Vous pouvez désormais utiliser Microsoft Access pour manipuler les données dans les tables Visual FoxPro importées. Les données que vous importez sont une capture instantanée des données stockées dans Visual FoxPro. les modifications que vous apportez aux données importées ne sont pas renvoyées à la source de données Visual FoxPro.  
  
 Si vous souhaitez que les modifications que vous apportez à Microsoft Access modifient les données de la source de données Visual FoxPro, consultez [interrogation et mise à jour des données Visual FoxPro à partir de Microsoft Access](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md).
