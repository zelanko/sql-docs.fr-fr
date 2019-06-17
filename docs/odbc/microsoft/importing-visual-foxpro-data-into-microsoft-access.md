---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f19b58ba93c94088c4cae19f1093d89c8decb843
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62471300"
---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>Importation de données Visual FoxPro dans Microsoft Access
Vous pouvez importer des données stockées dans une base de données Visual FoxPro dans une base de données Microsoft Access à l’aide de l’option d’importation.  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>Pour importer des données Visual FoxPro dans une base de données Microsoft Access  
  
1.  Ouvrez une base de données Microsoft Access.  
  
2.  Dans le menu fichier, choisissez que puis importer des données externes.  
  
3.  Dans la boîte de dialogue Importer, sélectionnez les bases de données ODBC dans la liste de type de fichiers.  
  
4.  Dans la boîte de dialogue Sources de données SQL, sélectionnez la source de données Visual FoxPro qui se connecte aux données FoxPro que vous souhaitez interroger et cliquez sur OK.  
  
5.  Dans la boîte de dialogue Importer des objets, sélectionnez un ou plusieurs tables à importer, cliquez sur OK. Les noms des tables Visual FoxPro que vous importés sont affichés dans l’onglet Tables de la base de données Microsoft Access.  
  
 Vous pouvez désormais utiliser Microsoft Access pour manipuler les données dans les tables Visual FoxPro importées. Les données que vous importez sont un instantané des données stockées dans Visual FoxPro ; modifications apportées aux données importées ne sont pas renvoyées à la source de données Visual FoxPro.  
  
 Si vous souhaitez que les modifications que vous apportez dans Microsoft Access pour modifier les données sur la source de données Visual FoxPro, consultez [interrogation et la mise à jour Visual FoxPro des données de Microsoft Access](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md).
